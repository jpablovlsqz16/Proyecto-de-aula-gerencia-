# Supuestos para la Simulación de Datos

**Proceso de pan trenza · Panadería San Nicolás**  
Proyecto de Aula 2026-2 · Gerencia de Proyectos · Ingeniería Industrial · Universidad de Medellín

Los datos se simulan con autorización del docente. Cada parámetro es un supuesto basado en el proceso típico de pan trenza y en la literatura de simulación; antes de generar los datos definitivos, conviene validar con la panadería los valores marcados en la última sección.

---

## 1. Objetivo y alcance

Generar un mes de datos del proceso de pan trenza de la Panadería San Nicolás con la estructura de la plantilla `Base_Panaderia_Indicadores.xlsx`, para calcular los cuatro indicadores del tablero: OEE del horno, SLA de pedidos, % de producto no vendido y productividad de mano de obra.

| Parámetro | Detalle |
|---|---|
| Horizonte | 1 mes: los 22 días hábiles (lunes a viernes) de septiembre de 2026 |
| Turnos | T1 06:00–14:00 y T2 14:00–22:00, de 480 min cada uno con 30 min de descanso → 44 turnos |
| Producto | PR_01 · Pan trenza de 350 g |
| Operarios | Máximo 2 por turno en el proceso de pan trenza |
| Método | Simulación de Montecarlo en Excel: cada dato se obtiene de una distribución de probabilidad con números aleatorios (ALEATORIO) |

---

## 2. Parámetros fijos (tablas Dim)

| Tabla | Campo | Valor | Justificación |
|---|---|---|---|
| Dim_Producto | tiempo_horneado_min | 22 | Horneado típico de 20–25 min a 170–180 °C |
| Dim_Producto | unidades_por_tanda | 16 | 4 latas × 4 trenzas (supuesto del horno) |
| Dim_Turno | duracion_min / descanso_min | 480 / 30 | Turnos definidos por el equipo |
| Dim_MotivoParo | MP_01 a MP_07 | Catálogo de la plantilla | Motivos típicos de paro del horno |
| Dim_MotivoParo | MP_08 Horno asignado a otros productos | Planeado · S | El horno también hornea otros panes; ese tiempo no es tiempo programado del pan trenza |

**Tiempo ideal por unidad** = 22 ÷ 16 = 1,375 min por trenza. Con 3 minutos de carga y descarga, cada tanda ocupa unos 25 minutos de horno.

### Ventana de horno asignada al pan trenza
El horno se comparte con otros productos. Se asume que el pan trenza tiene asignados 300 min en T1 y 240 min en T2. Ese es su tiempo programado; el resto del turno se registra como paro MP_08 (excluido), junto con el precalentamiento y la limpieza.

---

## 3. Distribuciones de las variables aleatorias

Criterio general, siguiendo la práctica de simulación: los conteos de eventos (pedidos, paros) se modelan con Poisson; las demandas de productos perecederos con binomial negativa o su aproximación normal; los tiempos entre fallas con exponencial y los tiempos de reparación con lognormal; los defectos con binomial; y cuando solo se conoce un mínimo, un valor más probable y un máximo, con la distribución triangular.

| Variable | Tabla | Distribución y parámetros | Justificación |
|---|---|---|---|
| Demanda de mostrador por día | Fact_Ventas | Binomial negativa; media por día de la semana: lun 170, mar 160, mié 165, jue 175, vie 210; coeficiente de variación del 15 % | La demanda diaria de productos perecederos suele presentar sobredispersión y efecto del día de la semana; la Poisson es su caso límite (Farrington y otros, 2023; SWI, 2024). |
| Número de pedidos por día | Fact_Pedidos | Poisson (λ = 3) | Llegadas independientes de eventos en un intervalo. |
| Cantidad por pedido | Fact_Pedidos | Uniforme discreta entre 10 y 40 trenzas | Solo se conoce un rango razonable de tamaño de pedido. |
| Hora comprometida de entrega | Fact_Pedidos | Uniforme discreta entre las 7:00 y las 18:00 | Pedidos repartidos a lo largo del día. |
| Desfase de la entrega | Fact_Pedidos | Normal (media −15 min, desviación 10 min) | Las entregas suelen salir antes de la hora acordada; con estos valores, cerca del 7 % llega tarde. |
| Pedido completo | Fact_Pedidos | Bernoulli (p = 0,97); si es incompleto, faltan entre 1 y 5 unidades | Evento sí/no con baja probabilidad de faltantes. |
| Producción planeada | Fact_Produccion | Media de demanda del día × 1,10 + unidades de pedidos; 60 % en T1 y 40 % en T2 | Colchón de seguridad del 10 % típico en panadería. |
| Duración real de cada tanda | Fact_Produccion | Normal (media 25 min, desviación 1,5 min), truncada entre 22 y 30 | Horneado más carga y descarga, con variación pequeña y simétrica. |
| Unidades defectuosas por tanda | Fact_Produccion | Binomial (n = 16, p = 0,04) | Cada trenza sale buena o defectuosa de forma independiente (control estadístico de calidad por atributos). |
| Número de paros no planeados por turno | Fact_Paros | Poisson (λ = 1) | Equivale a tiempos entre fallas exponenciales, el supuesto estándar en sistemas reparables. |
| Tipo de paro no planeado | Fact_Paros | Discreta: falta de masa 50 %, falla del horno 20 %, falta de personal 20 %, falta de gas 10 % | Proporciones supuestas a validar con la panadería. |
| Duración: falla del horno | Fact_Paros | Lognormal (media 30 min, desviación 15 min) | Los tiempos de reparación suelen ajustarse a una lognormal: muchos arreglos cortos y pocos largos. |
| Duración: falta de gas o energía | Fact_Paros | Lognormal (media 40 min, desviación 20 min) | Igual que una reparación: sesgo a la derecha. |
| Duración: falta de masa | Fact_Paros | Triangular (mín. 5, moda 10, máx. 25 min) | Retraso de la fermentación; sin datos, se usan mínimo, más probable y máximo. |
| Duración: falta de personal | Fact_Paros | Triangular (mín. 10, moda 20, máx. 40 min) | Igual criterio que la falta de masa. |
| Precalentamiento (solo T1) | Fact_Paros | Uniforme continua entre 20 y 30 min | Solo se conoce el rango. |
| Limpieza programada | Fact_Paros | Uniforme continua entre 10 y 20 min por turno | Solo se conoce el rango. |
| Asistencia de cada operario | Fact_ManoObra | Bernoulli (p = 0,97 de asistir) | Ausentismo bajo; si falta uno, el turno trabaja con 1 operario. |
| Horas trabajadas | Fact_ManoObra | Normal (media 7,5 h, desviación 0,25 h), truncada entre 6 y 8 y redondeada a 0,25 h | Jornada de 8 h menos descanso, con variación pequeña. |

---

## 4. Reglas de coherencia

Estas reglas evitan datos imposibles que darían indicadores por encima del 100 %:
- **Tiempo disponible del turno para hornear** = ventana asignada − paros no planeados.
- **Número de tandas** = el menor entre el necesario para la producción planeada (planeada ÷ 16, redondeado hacia arriba) y el que cabe en el tiempo disponible (disponible ÷ 25, redondeado hacia abajo).
- Las tandas se programan una tras otra; los paros se ubican entre tandas.
- **Ventas del día** = el menor entre (demanda de mostrador + unidades entregadas en pedidos) y las unidades buenas producidas.
- Los pedidos se atienden primero; si no alcanza el producto, la cantidad entregada se reduce.
- Ningún turno tiene más de 2 operarios ni más de 8 horas por persona.
- Se verifica que Disponibilidad, Rendimiento, Calidad, SLA y % no vendido queden entre 0 % y 100 %.

---

## 5. Fórmulas en Excel

`ALEATORIO()` genera un número uniforme entre 0 y 1. Con él y la inversa de cada distribución se obtiene el valor simulado.

| Distribución | Fórmula en Excel (versión en español) |
|---|---|
| Normal (μ, σ) | `=DISTR.NORM.INV(ALEATORIO(); μ; σ)` |
| Normal truncada [a, b] | `=MIN(b; MAX(a; DISTR.NORM.INV(ALEATORIO(); μ; σ)))` |
| Demanda (binomial negativa, aproximación normal) | `=MAX(0; REDONDEAR(DISTR.NORM.INV(ALEATORIO(); μ; 0,15*μ); 0))` |
| Poisson (λ) para λ pequeño | `=INV.BINOM(1000; λ/1000; ALEATORIO())` (binomial con n grande y p pequeño ≈ Poisson) |
| Binomial (n, p) | `=INV.BINOM(n; p; ALEATORIO())` |
| Bernoulli (p) | `=SI(ALEATORIO()<p; 1; 0)` |
| Uniforme discreta [a, b] | `=ALEATORIO.ENTRE(a; b)` |
| Uniforme continua [a, b] | `=a+(b-a)*ALEATORIO()` |
| Lognormal (media m, desviación s) | `=INV.LOGNORM(ALEATORIO(); LN(m^2/RAIZ(m^2+s^2)); RAIZ(LN(1+s^2/m^2)))` |
| Triangular (a, c, b) con u = ALEATORIO() | `=SI(u<(c-a)/(b-a); a+RAIZ(u*(b-a)*(c-a)); b-RAIZ((1-u)*(b-a)*(b-c)))` |
| Discreta (tipo de paro) | Con u = ALEATORIO(): `=SI(u<0,5;"MP_04";SI(u<0,7;"MP_05";SI(u<0,9;"MP_07";"MP_06")))` |

En Excel en inglés las funciones equivalentes son `NORM.INV`, `RAND`, `BINOM.INV`, `RANDBETWEEN`, `LOGNORM.INV`, `SQRT` e `IF`. Parámetros lognormales calculados: falla del horno μ = 3,290 y σ = 0,472; falta de gas μ = 3,577 y σ = 0,472.  
`ALEATORIO()` cambia cada vez que Excel recalcula. Después de generar los datos, copien y peguen como valores para congelarlos; así los indicadores no cambian y los resultados son reproducibles.

---

## 6. Procedimiento paso a paso

1. **Llenar las tablas Dim:** `Dim_Producto` con `PR_01`, `Dim_Turno` con `T1` y `T2`, y `Dim_MotivoParo` con `MP_01` a `MP_08`.
2. **Crear el calendario:** los 22 días hábiles de septiembre de 2026 × 2 turnos = 44 filas de turno.
3. **Simular los pedidos de cada día:** (número, cantidad, hora comprometida, entrega y completitud) → `Fact_Pedidos`.
4. **Simular la demanda de mostrador:** y calcular la producción planeada de cada turno.
5. **Simular los paros planeados:** (precalentamiento, limpieza, `MP_08`) y los no planeados con su tipo y duración → `Fact_Paros`.
6. **Calcular el número de tandas:** con las reglas de coherencia y simular la duración y los defectos de cada tanda → `Fact_Produccion`.
7. **Calcular las ventas de cada día:** → `Fact_Ventas`.
8. **Simular la asistencia y las horas de los operarios:** de cada turno → `Fact_ManoObra`.
9. **Pegar como valores:** revisar las reglas de coherencia y cargar el archivo en la aplicación.

---

## 7. Resultados esperados (validación)

Si la simulación está bien construida, los indicadores del mes deben quedar cerca de estos valores. Si se alejan mucho, hay un error en las fórmulas.

| Indicador | Valor esperado | Por qué |
|---|---|---|
| Disponibilidad | ≈ 92 % | Unos 20–25 min de paros no planeados por turno |
| Rendimiento | ≈ 72 % a 80 % | Ventana de horno mayor que la necesaria y 3 min de carga por tanda |
| Calidad | ≈ 96 % | p = 0,04 de defectos |
| OEE | ≈ 65 % a 70 % | Producto de los tres componentes |
| SLA | ≈ 90 % | 7 % de entregas tardías y 3 % de pedidos incompletos |
| % no vendido | ≈ 8 % a 10 % | Colchón de producción del 10 % |
| Productividad | ≈ 8 a 9 trenzas por hora-hombre | Unas 130 trenzas buenas por turno con 15 horas-hombre |

---

## 8. Datos que deben validarse con la panadería

Con estos datos reales, aunque sean aproximados, los parámetros dejan de ser supuestos del equipo y pasan a estar respaldados por el usuario:

| Dato a preguntar | Parámetro que ajusta |
|---|---|
| ¿Cuántas trenzas caben en una horneada y cuánto dura? | `unidades_por_tanda` y `tiempo_horneado_min` |
| ¿Cuánto tiempo del horno se dedica al pan trenza en cada turno? | Ventana asignada (300 y 240 min) |
| ¿Cuántas trenzas se venden un día normal y un viernes? | Medias de demanda por día |
| ¿Cuántos pedidos llegan al día y de qué tamaño? | λ de pedidos y rango de cantidad |
| ¿Cuántas trenzas salen malas en una horneada típica? | p de defectos |
| ¿Cada cuánto se para el horno y por qué? | λ de paros y proporciones por tipo |
| ¿Cuánto se demora en arreglarse el horno? | Media y desviación de la lognormal |
| ¿Cuántas personas trabajan por turno y cuántas horas? | Operarios y horas trabajadas |

---

## Referencias

- Farrington, J., Li, K., Wong, W. K. y Utley, M. (2023). *Going faster to see further: GPU-accelerated value iteration and simulation for perishable inventory control using JAX*. arXiv. https://arxiv.org/pdf/2303.10672
- Study Group Mathematics with Industry (SWI). (2024). *Scientific proceedings*. https://swi-wiskunde.nl/swi2024/wp-content/uploads/sites/29/2024/06/SWI-2024-scientific-proceedings_TDF.pdf
- *Confidence intervals for steady state availability of a system with exponential operating time and lognormal repair time*. Applied Mathematics and Computation, 328. https://www.datalearner.com/academic/journal-papers/0096-3003/volumes-and-issues/328/paper-detail/43020
- *Transient behavior of time-between-failures of complex repairable systems*. https://iaorifors.com/paper/38583
- Standridge, C. R. *Beyond Lean: Simulation in Practice*. Cap. 3.2, Determining a distribution in the absence of data. https://eng.libretexts.org/Bookshelves/Industrial_and_Systems_Engineering/Beyond_Lean_-_Simulation_in_Practice_(Standridge)
- Winter Simulation Conference. (2011). *Paper 324, sobre el uso de estimaciones de expertos en la distribución triangular*. https://www.informs-sim.org/wsc11papers/324.pdf
- Law, A. M. (2015). *Simulation modeling and analysis* (5.ª ed.). McGraw-Hill.
- Montgomery, D. C. (2019). *Introduction to statistical quality control* (8.ª ed.). Wiley.
