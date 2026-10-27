# Desarrollo de la Primera Entrega

**Tablero de Indicadores · Panadería San Nicolás (pan trenza)**  
Proyecto de Aula 2026-2 · Gerencia de Proyectos · Ingeniería Industrial · Universidad de Medellín

Este documento desarrolla las historias de usuario de la primera entrega, excepto las relacionadas con la aplicación (HU-13 repositorio, HU-14 arquitectura y HU-16 prototipo v0). Los datos marcados como `[completar]` deben confirmarse con la Panadería San Nicolás, y las cifras marcadas como supuesto deben validarse con el dueño antes de entregarse.

---

## HU-01 · Información de la empresa y del proceso

### La empresa

| Concepto | Detalle |
|---|---|
| Razón social | Panadería San Nicolás |
| Sector | Alimentos · panificación de punto caliente (produce y vende en el mismo local) |
| Tamaño | Microempresa |
| Ubicación | `[completar: barrio y municipio]` |
| Productos | Panes de sal y de dulce, pastelería y pedidos por encargo. El proceso monitoreado es el pan trenza. |
| Clientes | Clientes de mostrador del barrio y clientes con pedidos (tiendas, cafeterías y encargos para eventos). |
| Operación | 2 turnos de 8 horas (06:00–14:00 y 14:00–22:00), 22 días al mes, con máximo 2 operarios por turno en el proceso de pan trenza. |
| Equipo crítico | Horno de latas, con capacidad de 16 trenzas por tanda (supuesto a confirmar). Es el cuello de botella del proceso. |

### El proceso de pan trenza

El pan trenza es un pan dulce enriquecido con huevo, mantequilla y azúcar, trenzado de 3 hebras y de unos 350 g. El proceso completo dura entre 3 y 3,5 horas por lote, de las cuales unos 22 minutos son de horneado.

| # | Etapa | Descripción | Tiempo aprox. |
|---|---|---|---|
| 1 | Recepción de insumos | Recibir y almacenar harina, huevo, azúcar, mantequilla y levadura. | Variable |
| 2 | Pesaje | Pesar los ingredientes según la fórmula. | 10 min |
| 3 | Mezclado y amasado | Mezclar y amasar hasta desarrollar el gluten. | 12–15 min |
| 4 | Primera fermentación | Reposo de la masa en bloque. | 20–30 min |
| 5 | División y boleado | Cortar porciones de unos 115 g y bolear. | 15–20 min |
| 6 | Formado (trenzado) | Estirar las tiras y trenzar de 3 hebras. | 2–3 min por trenza |
| 7 | Fermentación final | Crecimiento en lugar tibio hasta casi doblar el volumen. | 45–60 min |
| 8 | Barnizado y decoración | Barnizar con huevo y decorar con azúcar o ajonjolí. | 5 min |
| 9 | Horneado | Horno a 170–180 °C. | 20–25 min |
| 10 | Enfriamiento | Reposo en rejillas. | 30–45 min |
| 11 | Empaque | Empacar, exhibir en vitrina o despachar pedidos. | Variable |

### Operación y proyecto

La operación es producir pan trenza todos los días: es permanente, repetitiva y se mide por eficiencia. El proyecto es desarrollar el tablero de indicadores: es temporal (julio a octubre de 2026), produce un resultado único y se mide por alcance, tiempo, costo y beneficio. El proyecto crea la capacidad de medir; la operación la usa todos los días.

---

## HU-02 · SIPOC del proceso de pan trenza

| Proveedores (S) | Entradas (I) | Proceso (P) | Salidas (O) | Clientes (C) |
|---|---|---|---|---|
| - Molino o distribuidor de harina<br>- Proveedor de huevos<br>- Distribuidor de lácteos (mantequilla, leche)<br>- Proveedor de levadura y azúcar<br>- Empresa de gas<br>- Empresa de energía<br>- Empaques | - Harina de trigo<br>- Huevo<br>- Azúcar<br>- Mantequilla<br>- Leche o agua<br>- Levadura<br>- Sal<br>- Gas y energía<br>- Mano de obra (2 operarios por turno)<br>- Receta estándar<br>- Pedidos y plan de producción | 1. Recepción<br>2. Pesaje<br>3. Mezclado<br>4. Amasado<br>5. División<br>6. Formado<br>7. Fermentación<br>8. Horneado<br>9. Enfriamiento<br>10. Empaque | - Pan trenza empacado (unidades buenas)<br>- Producto defectuoso (quemado, crudo, deforme)<br>- Pedidos despachados<br>- Registros de producción, paros, ventas y pedidos | - Clientes de mostrador<br>- Tiendas y cafeterías<br>- Clientes con encargos para eventos<br>- Administración de la panadería (usa los registros y el tablero) |

---

## HU-03 · Estrategia corporativa

*Misión, visión y objetivos propuestos por el equipo. Validarlos con el dueño de la panadería.*

| Elemento | Definición |
|---|---|
| Misión | Elaborar pan fresco y de calidad todos los días para las familias y negocios del barrio, con recetas tradicionales, atención cercana y uso responsable de los recursos. |
| Visión | Ser en 2030 la panadería de referencia del sector, reconocida por la calidad de sus productos, el cumplimiento a sus clientes y una gestión basada en datos. |

### Objetivos estratégicos

| # | Objetivo estratégico | Indicador | Meta |
|---|---|---|---|
| OE1 | Reducir el desperdicio de producto no vendido. | % producto no vendido | ≤ 10 % |
| OE2 | Cumplir a tiempo y completos los pedidos de los clientes. | SLA (OTIF) | ≥ 95 % |
| OE3 | Aumentar la eficiencia del horno, equipo cuello de botella. | OEE del horno | ≥ 65 % |
| OE4 | Mejorar la productividad del personal. | Productividad de mano de obra | Línea base + 5 % |
| OE5 | Digitalizar la gestión de la producción. | Tablero en uso diario | 100 % de los turnos registrados |

La aplicación aporta directamente al OE5 (digitalizar la gestión) y es el medio para medir y mejorar los otros cuatro: sin datos, no se puede saber si el desperdicio baja, si los pedidos llegan a tiempo, si el horno se usa bien o si el personal es más productivo.

---

## HU-04 · Portafolio, programas y proyectos

| Nivel | Componente | Pregunta de gestión y beneficio |
|---|---|---|
| Portafolio | Portafolio de la Panadería San Nicolás: todos los programas, proyectos y la operación diaria de producción y venta. | ¿Estamos haciendo los proyectos correctos? Beneficio: crecimiento rentable y sostenible. |
| Programa 1 | Transformación digital: (a) tablero de indicadores de producción ← nuestro proyecto; (b) sistema de punto de venta e inventario; (c) toma de pedidos por WhatsApp. | ¿Coordinamos bien los proyectos digitales? Beneficio: decisiones basadas en datos. Los proyectos se relacionan porque comparten los mismos datos de producción y ventas. |
| Programa 2 | Productividad y calidad: (a) estandarización de la receta de pan trenza; (b) mantenimiento preventivo del horno; (c) capacitación de operarios. | ¿Mejoramos la eficiencia del proceso? Beneficio: más producto bueno por hora. Los proyectos se relacionan porque todos actúan sobre el OEE y la productividad. |
| Programa 3 | Sostenibilidad: (a) reducción y donación de pan no vendido; (b) uso eficiente del gas. | ¿Reducimos el impacto ambiental? Beneficio: menos desperdicio y menos costo. |
| Operación | Producción y venta diaria de pan. | No es un proyecto: es permanente. Hace parte del portafolio. |
| Proyecto | Tablero de indicadores de producción de pan trenza. | ¿Estamos haciendo bien el proyecto? Se mide por alcance, tiempo, costo y beneficio. |

---

## HU-05 · Clasificación del proyecto y ciclo de vida

### Clasificación descriptiva

| Criterio | Clasificación |
|---|---|
| Finalidad | Con ánimo de lucro (beneficia a una empresa privada); además tiene fin académico. |
| Origen de los recursos | Privado: recursos propios del equipo y de la panadería. |
| Sector u objeto | Productivo, con componente de tecnología de la información. |
| Tamaño de la inversión | Pequeño. |
| Alcance territorial | Local. |
| Duración | Corto plazo (julio a octubre de 2026, unas 15 semanas). |
| Lugar en la estrategia | Dentro del programa Transformación digital del portafolio. |

### Clasificación por enfoque de entrega
**Híbrido.** La gestión del proyecto (acta, EDT, hitos de entrega del 8 de septiembre y del 29 de octubre, presupuesto) es predictiva, porque las fechas y los entregables están definidos por la guía del curso. El desarrollo de la aplicación es adaptativo (Scrum), porque los requisitos se descubren con el usuario y el docente entrega los criterios de aceptación en cada Sprint Planning.

### Perfil del proyecto: modelo Diamante

| Dimensión | Nivel | Justificación |
|---|---|---|
| Novedad | Derivativo | Mejora la gestión de un proceso que ya existe; los tableros de control son conocidos. |
| Tecnología | Baja | Usa tecnología madura y probada (Google Apps Script, Google Sheets). |
| Complejidad | Ensamble | Es un solo sistema pequeño con pocos componentes. |
| Ritmo | Rápido / crítico | Tiene fechas de entrega fijas que no se pueden mover. |

*Conclusión:* un proyecto derivativo, de tecnología baja y ensamble se puede planear, pero el ritmo crítico obliga a proteger las fechas y a priorizar el alcance.

### Ciclo de vida del proyecto

| Fase | Fechas | Entregables | Punto de decisión |
|---|---|---|---|
| 1. Formulación | 21 jul – 8 sep | Empresa, SIPOC, estrategia, estudios, business case, acta, EDT, riesgos, fichas de indicadores | Primera entrega (8 sep): ¿se continúa? |
| 2. Desarrollo | 9 sep – 25 oct | Aplicación construida por sprints | Sprint Review de cada sprint |
| 3. Pruebas y validación | 26 – 28 oct | Plan y evidencia de pruebas, validación con el usuario | ¿La aplicación funciona con un archivo nuevo? |
| 4. Cierre | 29 oct | Informe final, sustentación, lecciones aprendidas | Entrega final: aceptación del docente |

**Los tres ciclos:**
- **Ciclo de preinversión:** idea → perfil → prefactibilidad → factibilidad (HU-07 y HU-08). Decide si el proyecto nace.
- **Ciclo de vida del proyecto:** las 4 fases anteriores, de julio a octubre de 2026.
- **Ciclo de vida del producto:** empieza cuando la panadería usa el tablero y dura mientras lo siga usando, más allá del cierre del proyecto.

---

## HU-06 · ODS y responsabilidad social empresarial

### Contribución a los ODS

| Meta ODS | Contribución | Indicador | Línea base | Responsable y medición |
|---|---|---|---|---|
| 12.3 Reducir el desperdicio de alimentos | Medir el pan no vendido para ajustar la producción a la demanda. | % producto no vendido | Primer mes de medición | Administrador · mensual |
| 8.2 Productividad mediante modernización tecnológica | Usar datos para mejorar la productividad del proceso. | Productividad de mano de obra y OEE | Primer mes de medición | Administrador · mensual |

### RSE: las siete materias de la ISO 26000

| Materia fundamental | Aplicación en el proyecto |
|---|---|
| Gobernanza de la organización | Decisiones de producción basadas en datos y responsables definidos para cada indicador. |
| Derechos humanos | El tablero mide procesos, no vigila personas: no se usa para sanciones individuales. |
| Prácticas laborales | Turnos de 8 horas que respetan la jornada legal; el registro de datos no agrega carga excesiva a los operarios. |
| Medio ambiente | Reducción del pan desperdiciado y del gas usado en horneadas innecesarias. |
| Prácticas justas de operación | Uso de software libre y gratuito con licencias respetadas. |
| Asuntos de consumidores | Protección de los datos de clientes con pedidos (Ley 1581 de 2012): se registra un código, no datos personales. |
| Desarrollo de la comunidad | Posible donación del pan no vendido apto para consumo a fundaciones del barrio. |

---

## HU-07 · Estudios de prefactibilidad y factibilidad

### Prefactibilidad: alternativas comparadas
Con información secundaria se compararon cinco alternativas: (A) no hacer nada, (B) registro manual en Excel, (C) Power BI, (D) software comercial de gestión para panaderías y (E) construir una aplicación propia en Google Apps Script. Las alternativas C y D se descartaron por costo de licencias y porque la guía del curso no admite como producto un archivo de Power BI, Looker Studio o Excel sin desarrollo propio. La alternativa A se mantiene como base de comparación. Pasa a factibilidad la alternativa E.

### Factibilidad: los siete estudios de la alternativa elegida

| Estudio | Hallazgos | Conclusión |
|---|---|---|
| Mercado | En Colombia hay cerca de 25.000 panaderías, de las cuales el 67 % son de punto caliente (Adepan, citado por El País, 2025). La mayoría son pequeñas y no usan herramientas de análisis de datos. La necesidad de medir desperdicio y eficiencia es común en el sector. | Pasa |
| Técnico | Google Apps Script y Google Sheets permiten construir y publicar una aplicación web sin servidor. Solo se requiere un computador o celular con internet y una cuenta de Google. El equipo tiene conocimientos de JavaScript. | Pasa |
| Legal y regulatorio | Protección de datos personales (Ley 1581 de 2012): no se registran datos personales de clientes. Derechos de autor del software (Ley 23 de 1982). Licencias libres (Chart.js, MIT). Términos de uso de Google. No requiere permisos ni licencias. | Pasa |
| Ambiental | No requiere licencia ambiental. Impacto positivo: menos pan desperdiciado y menos gas en horneadas innecesarias. | Pasa |
| Social y de interesados | Los operarios podrían ver el registro de datos como control. Se mitiga comunicando que se miden procesos, no personas, e involucrándolos en el diseño de la planilla. | Pasa con condiciones |
| Organizacional | Los operarios registran los datos en una planilla (unos 10 minutos por turno) y el administrador revisa el tablero (unos 15 minutos por día). No requiere contratar personal. | Pasa |
| Financiero | Costo en efectivo para la panadería cercano a $0. Beneficio estimado de $432.000 al mes por reducción del pan no vendido (ver HU-08). | Pasa |

**Capa transversal:**
- **Riesgo:** registro de riesgos en la HU-11.
- **Sostenibilidad:** contribución a las metas ODS 12.3 y 8.2 (HU-06).
- **Beneficios:** cada beneficio tiene indicador, línea base, responsable y momento de medición (HU-08).

*Conclusión:* el proyecto es factible. Ninguno de los siete estudios arroja un "no".

---

## HU-08 · Business case

### 1. Problema u oportunidad
La panadería no mide su desempeño: no sabe cuánto pan trenza se desperdicia, cuánto tiempo pierde el horno ni si cumple los pedidos. Las decisiones sobre cuánto producir se toman por intuición, lo que genera sobreproducción o agotados. El problema se alinea con los objetivos estratégicos OE1 a OE5.

### 2. Alternativas evaluadas

| Alternativa | Costo inicial | Costo mensual | Ajuste a la necesidad | Decisión |
|---|---|---|---|---|
| A. No hacer nada | $0 | $0 | No resuelve el problema; se mantiene la pérdida | Base de comparación |
| B. Excel manual | $0 | ≈ 22 h/mes del administrador | Bajo: cálculo manual y propenso a errores | Descartada |
| C. Power BI | Desarrollo por un tercero | USD 14 por usuario (Pro) | Medio; no admitido como producto del curso | Descartada |
| D. Software comercial | Variable | Suscripción mensual | Medio: genérico, no mide OEE del horno | Descartada |
| E. Aplicación propia | $4,8 M (horas del equipo) | ≈ $40.000 (mantenimiento) | Alto: hecha a la medida del proceso | Recomendada |

### 3. Alternativa recomendada
**E. Aplicación propia en Google Apps Script.** Criterios: costo de licencias $0, ajuste al proceso de pan trenza, facilidad de uso para la panadería, sostenibilidad (la panadería puede seguir usándola con una cuenta gratuita) y cumplimiento de la guía del curso.

### 4. Beneficios esperados

| Beneficio | Indicador | Línea base | Meta | Responsable / medición |
|---|---|---|---|---|
| Menos pan no vendido | % producto no vendido | 12 % (supuesto) | ≤ 10 % | Administrador · mensual |
| Mejor cumplimiento de pedidos | SLA | Primer mes | ≥ 95 % | Administrador · mensual |
| Mejor uso del horno | OEE | Primer mes | ≥ 65 % | Administrador · mensual |
| Más productividad | Unidades buenas por hora-hombre | Primer mes | Línea base + 5 % | Administrador · mensual |

### Cálculo del beneficio y VPN

| Concepto | Valor |
|---|---|
| Producción mensual de pan trenza (supuesto) | ≈ 5.760 unidades (262 por día × 22 días) |
| Reducción del no vendido | Del 12 % al 9 % = 3 puntos ≈ 173 unidades al mes |
| Costo de producción por unidad (supuesto) | $2.500 |
| Ahorro mensual | 173 × $2.500 ≈ $432.000 |
| Mantenimiento mensual | 2 h × $20.000 = $40.000 |
| Flujo neto mensual | $392.000 |
| Inversión (240 h del equipo × $20.000/h, costo de oportunidad) | $4.800.000 |
| Tasa de descuento | 12 % efectivo anual (0,949 % mensual) |
| VPN a 12 meses | −$4.800.000 + $392.000 × 11,291 ≈ −$374.000 |
| VPN a 24 meses | −$4.800.000 + $392.000 × 21,373 ≈ +$3.578.000 |
| Periodo de recuperación | Unos 13 meses |

Para la panadería el costo en efectivo es casi nulo, porque el desarrollo lo hace el equipo como proyecto académico. Valorando las horas del equipo como costo de oportunidad, el proyecto crea valor a partir del segundo año.

### 5. Supuestos, riesgos y restricciones
- **Supuestos:** producción y costo unitario estimados; la panadería registra los datos todos los turnos; el tablero se usa para ajustar la producción.
- **Riesgos:** ver la HU-11.
- **Restricciones:** fecha de entrega fija (29 de octubre), presupuesto en efectivo cercano a cero y equipo de 4 personas con otras materias.

### 6. Recursos solicitados
Unas 240 horas del equipo entre julio y octubre de 2026, una cuenta de Google y acceso a los registros (simulados con autorización del docente) del proceso de pan trenza.

### Criterios de éxito
1. La aplicación genera el tablero con un archivo distinto en la demostración del 29 de octubre.
2. Los 4 indicadores coinciden con un cálculo manual de verificación.
3. El usuario valida que el tablero le sirve para decidir.
4. El proyecto se entrega en la fecha comprometida.

---

## HU-09 · Acta de constitución del proyecto

| Campo | Contenido |
|---|---|
| Nombre del proyecto | Tablero de indicadores de producción de pan trenza – Panadería San Nicolás |
| Fecha | `[completar: fecha de aprobación]` |
| Patrocinador | Dueño de la Panadería San Nicolás `[completar nombre]`: aprueba el uso de la aplicación y aporta la información del proceso. |
| Product Owner | Ronal Alexander Álvarez Valencia (docente): prioriza el backlog y entrega los criterios de aceptación. |
| Líder del proyecto | Juan Pablo (Scrum Master): coordina al equipo y responde por el avance. Puede aprobar cambios que no afecten fechas ni alcance; los demás los decide el Product Owner. |
| Equipo | María Camila (QA), Juan José (desarrollador), Iván Santiago (desarrollador). |
| Justificación | La panadería no mide su desempeño y toma decisiones de producción sin datos (ver business case). |
| Objetivo | Desarrollar, a más tardar el 29 de octubre de 2026, una aplicación que genere un tablero con 4 indicadores (OEE, SLA, % no vendido y productividad) del proceso de pan trenza a partir de un archivo de datos. |
| Alcance de alto nivel | Formulación del proyecto, modelo de datos, simulación de datos, aplicación web con carga de archivo, cálculo de indicadores y tablero, pruebas y validación. |
| Entregables | Informe de la primera entrega, aplicación funcional, informe final, anexos obligatorios y sustentaciones. |
| Hitos | 21 jul: inicio · 8 sep: primera entrega y sustentación · 29 oct: entrega final, sustentación y demostración. |
| Presupuesto resumido | $4.800.000 en horas del equipo (costo de oportunidad) + reserva de contingencia del 10 % ($480.000). Costo en efectivo cercano a $0. |
| Supuestos | El equipo dedica unas 4 horas por semana por persona; los datos se simulan con autorización del docente; las herramientas de Google siguen siendo gratuitas. |
| Restricciones | Fechas fijas; máximo 3 integrantes según la guía (el equipo debe confirmar su conformación con el docente); informe de máximo 10 páginas. |
| Criterios de éxito | Los cuatro de la HU-08. |
| Aprobación | Patrocinador: ______________ &nbsp;&nbsp;&nbsp; Product Owner: ______________ &nbsp;&nbsp;&nbsp; Líder: ______________ |

### Registro de interesados

| Interesado | Interés en el proyecto | Poder | Interés | Estrategia |
|---|---|---|---|---|
| Dueño de la panadería | Reducir pérdidas y tomar mejores decisiones | Alto | Alto | Gestionar de cerca; validar resultados |
| Administrador | Usar el tablero cada día | Medio | Alto | Involucrar en el diseño y en las pruebas |
| Operarios (2 por turno) | Que el registro sea fácil y no los perjudique | Medio | Alto | Informar y capacitar; explicar que se miden procesos, no personas |
| Clientes con pedidos | Recibir los pedidos a tiempo y completos | Bajo | Medio | Monitorear con el SLA |
| Docente (Product Owner) | Que el proyecto cumpla la guía | Alto | Alto | Gestionar de cerca; Sprint Reviews |
| Equipo del proyecto | Aprobar y aprender | Medio | Alto | Dailies y retrospectivas |

---

## HU-10 · EDT y líneas base

### Enunciado del alcance
El proyecto entrega una aplicación web que carga un archivo de datos del proceso de pan trenza, valida su estructura, calcula OEE, SLA, % no vendido y productividad de mano de obra, y los muestra en un tablero con filtros y semáforos. Incluye la formulación del proyecto, la simulación de datos y la documentación exigida por la guía.

**Exclusiones explícitas:** otros productos distintos del pan trenza; integración con sistemas de punto de venta, inventario o contabilidad; aplicación móvil nativa; compra de hardware; captura automática de datos con sensores; manejo de datos personales de clientes; soporte y mantenimiento después del 29 de octubre de 2026.

### EDT (tres niveles)

| Código | Nivel 2 | Nivel 3 (paquetes de trabajo) |
|---|---|---|
| 1.1 | Gestión del proyecto | 1.1.1 Acta de constitución · 1.1.2 EDT, cronograma y presupuesto · 1.1.3 Gestión de riesgos · 1.1.4 Seguimiento Scrum · 1.1.5 Cierre y lecciones aprendidas |
| 1.2 | Formulación | 1.2.1 Empresa, proceso y SIPOC · 1.2.2 Estrategia y portafolio · 1.2.3 Clasificación, ODS y RSE · 1.2.4 Estudios de prefactibilidad y factibilidad · 1.2.5 Business case |
| 1.3 | Datos | 1.3.1 Modelo y diccionario de datos · 1.3.2 Simulación de datos · 1.3.3 Fichas técnicas de indicadores |
| 1.4 | Aplicación | 1.4.1 Arquitectura · 1.4.2 Prototipo v0 · 1.4.3 Carga y validación de archivos · 1.4.4 Cálculo de indicadores · 1.4.5 Tablero, filtros y semáforos |
| 1.5 | Pruebas y validación | 1.5.1 Plan y evidencia de pruebas · 1.5.2 Validación con el usuario |
| 1.6 | Entregas | 1.6.1 Primera entrega (informe y sustentación) · 1.6.2 Entrega final (informe, sustentación y demostración) |

*El nivel 1 es el proyecto completo: 1. Tablero de indicadores – Panadería San Nicolás.*

### Línea base de cronograma

| Entregable | Inicio | Fin | Horas est. |
|---|---|---|---|
| 1.2 Formulación | 21 jul | 25 ago | 70 |
| 1.1 Gestión (acta, EDT, riesgos) | 28 jul | 1 sep | 30 |
| 1.3 Datos | 11 ago | 1 sep | 30 |
| 1.6.1 Primera entrega | 2 sep | 8 sep | 15 |
| 1.4 Aplicación | 9 sep | 25 oct | 60 |
| 1.5 Pruebas y validación | 26 oct | 28 oct | 15 |
| 1.6.2 Entrega final y cierre | 28 oct | 29 oct | 20 |
| **Total** | | | **240** |

### Línea base de costo
240 horas × $20.000 por hora (supuesto de costo de oportunidad) = $4.800.000, más una reserva de contingencia del 10 % ($480.000). Total: **$5.280.000**. Las horas reales de cada historia se registran para compararlas con lo estimado, como exige la guía.

---

## HU-11 · Gestión de riesgos

Escala de 1 a 5 para probabilidad (P) e impacto (I). Nivel = P × I: alto de 12 a 25, medio de 6 a 11, bajo de 1 a 5.

| # | Riesgo | P | I | Nivel | Respuesta | Responsable |
|---|---|---|---|---|---|---|
| R1 | La aplicación no procesa el archivo distinto del docente en la demostración (técnico). | 3 | 5 | Alto (15) | Mitigar: validación de estructura y pruebas con varios archivos, incluidos archivos con errores. | María Camila |
| R2 | Retraso en el desarrollo por carga académica de otras materias. | 4 | 4 | Alto (16) | Mitigar: sprints cortos, priorización MoSCoW y dailies. | Juan Pablo |
| R3 | Errores en el cálculo de los indicadores (técnico). | 3 | 4 | Alto (12) | Mitigar: comparar contra cálculos manuales en Excel. | Iván Santiago |
| R4 | Límites de ejecución de Google Apps Script con archivos grandes (técnico). | 2 | 4 | Medio (8) | Mitigar: procesar por lotes y limitar el tamaño del archivo. | Juan José |
| R5 | Datos simulados poco realistas que restan credibilidad. | 3 | 3 | Medio (9) | Mitigar: supuestos documentados y validados con la panadería. | María Camila |
| R6 | Un integrante abandona la materia o el equipo. | 2 | 4 | Medio (8) | Aceptar: documentación en el repositorio para redistribuir el trabajo. | Juan Pablo |
| R7 | Pérdida del código o de la información. | 2 | 5 | Medio (10) | Evitar: control de versiones en GitHub y copias en Google Drive. | Iván Santiago |
| R8 | Cambio en los criterios de aceptación entregados por el docente. | 3 | 3 | Medio (9) | Aceptar: repriorizar el backlog en el siguiente Sprint Planning. | Juan Pablo |
| R9 | Los operarios no registran los datos de forma constante. | 3 | 3 | Medio (9) | Mitigar: planilla simple de 10 minutos por turno y capacitación. | María Camila |
| R10 | Google cambia las condiciones gratuitas de Apps Script. | 1 | 4 | Bajo (4) | Aceptar: monitorear; el código es portable a otra plataforma. | Juan José |
| R11 | El informe supera las 10 páginas permitidas. | 3 | 2 | Medio (6) | Evitar: plantilla con extensión controlada y anexos. | Juan Pablo |
| R12 | Oportunidad: otras panaderías del barrio se interesan en la aplicación. | 2 | 3 | Medio (6) | Explotar: documentar la vía de escalamiento en el CANVAS. | Juan Pablo |

### Matriz de probabilidad e impacto

| P \ I | 1 | 2 | 3 | 4 | 5 |
|:---:|:---:|:---:|:---:|:---:|:---:|
| **5** | | | | | |
| **4** | | | | R2 | |
| **3** | | R11 | R5, R8, R9 | R3 | R1 |
| **2** | | | R12 | R4, R6 | R7 |
| **1** | | | | R10 | |

*Reserva de contingencia:* 10 % de la línea base de costo ($480.000), equivalente a unas 24 horas del equipo para atender los riesgos altos.

---

## HU-12 · Marco Scrum

### Roles

| Integrante | Rol | Responsabilidad |
|---|---|---|
| Ronal Alexander Álvarez Valencia (docente) | Product Owner | Prioriza el backlog y entrega los criterios de aceptación |
| Juan Pablo | Scrum Master | Facilita los eventos y elimina impedimentos; gestión y documentación |
| María Camila | QA | Pruebas, validación y apoyo en historias no técnicas |
| Juan José | Desarrollador | Desarrollo técnico de la aplicación |
| Iván Santiago | Desarrollador | Desarrollo técnico de la aplicación |

### Product Backlog priorizado
El backlog contiene las historias HU-01 a HU-16 de la primera entrega, cada una con descripción, criterios de aceptación y estimación en puntos de Fibonacci (anexo de historias de usuario). Se prioriza por valor para el Product Owner y por dependencias: primero la formulación, luego la gestión y por último la arquitectura y el prototipo.

### Sprints de la primera etapa
*Fechas propuestas. Ajústenlas a las fechas reales en que trabajaron.*

| Sprint | Fechas | Historias | Meta |
|---|---|---|---|
| Sprint 1 | 28 jul – 10 ago | HU-01 a HU-06 | Empresa, proceso, estrategia y clasificación |
| Sprint 2 | 11 ago – 24 ago | HU-07 a HU-11 | Estudios, business case, acta, EDT y riesgos |
| Sprint 3 | 25 ago – 7 sep | HU-12 a HU-16 | Scrum, arquitectura, fichas y prototipo v0 |

### Tablero
Tablero en Trello con las columnas: `Product Backlog` · `Por hacer (sprint)` · `En progreso` · `En revisión (QA)` · `Terminado`. Cada tarjeta es una historia de usuario con su checklist de criterios de aceptación, su responsable y sus puntos.

### Definición de terminado (DoD)
- Cumple todos sus criterios de aceptación.
- Fue revisada por QA.
- La información quedó en Google Sheets o en el informe.
- Los cambios están en el repositorio.
- La tarjeta está en "Terminado".
- Fue aceptada por el Product Owner en la Sprint Review.

Enlace al repositorio: `[completar]` · Enlace al tablero de Trello: `[completar]`

---

## HU-15 · Fichas técnicas de los indicadores

*Frecuencias: los datos se registran en cada turno, los indicadores se calculan por turno y por día, y se analizan cada semana y cada mes.*

### Indicador 1 · OEE del horno (Overall Equipment Effectiveness)

| Campo | Detalle |
|---|---|
| Nombre | OEE del horno (Overall Equipment Effectiveness) |
| Qué representa | La eficiencia real del horno frente a lo que podría producir si trabajara todo el tiempo programado, a su velocidad ideal y sin defectos. Integra en un solo número las pérdidas por paradas, por velocidad y por calidad. |
| Fórmula | OEE = Disponibilidad × Rendimiento × Calidad |
| Cómo se calcula | 1. Calcular la Disponibilidad, el Rendimiento y la Calidad del turno (fichas 1a, 1b y 1c).<br>2. Multiplicar los tres valores.<br>3. Para el día o el mes, sumar primero los tiempos y las unidades de todos los turnos y luego calcular; no promediar porcentajes. |
| Frecuencia | Cálculo por turno y por día; análisis semanal y mensual. |
| Unidad | % |
| Fuente de datos | Fact_Produccion, Fact_Paros, Dim_Turno, Dim_Producto, Dim_MotivoParo |
| Meta y semáforo | Verde ≥ 65 % · Amarillo 55 % a 65 % · Rojo < 55 % |
| Responsable | Administrador de la panadería |

#### Indicador 1a · Disponibilidad

| Campo | Detalle |
|---|---|
| Nombre | Disponibilidad |
| Qué representa | Qué proporción del tiempo programado el horno estuvo realmente operando. Mide las pérdidas por paradas no planeadas (fallas, falta de masa, falta de gas, falta de personal). |
| Fórmula | Disponibilidad = Tiempo operativo ÷ Tiempo programado |
| Cómo se calcula | 1. Tiempo programado = duración del turno − descanso − paros planeados excluidos (motivos con `excluir_tiempo_programado = S`).<br>2. Tiempo operativo = tiempo programado − paros no excluidos (`excluir = N`).<br>3. Dividir el tiempo operativo entre el programado. |
| Frecuencia | Cálculo por turno; análisis semanal. |
| Unidad | % |
| Fuente de datos | Dim_Turno, Fact_Paros, Dim_MotivoParo |
| Meta y semáforo | Verde ≥ 90 % · Amarillo 80 % a 90 % · Rojo < 80 % |
| Responsable | Administrador |

#### Indicador 1b · Rendimiento

| Campo | Detalle |
|---|---|
| Nombre | Rendimiento |
| Qué representa | Qué tan cerca de su velocidad ideal produjo el horno mientras estuvo operando. Mide las pérdidas por tandas más lentas, microparadas y tiempos muertos entre tandas. |
| Fórmula | Rendimiento = Σ(unidades producidas × tiempo ideal por unidad) ÷ Tiempo operativo |
| Cómo se calcula | 1. Tiempo ideal por unidad = tiempo_horneado_min ÷ unidades_por_tanda (para pan trenza: 22 ÷ 16 = 1,375 min).<br>2. Multiplicar las unidades producidas del turno por ese tiempo ideal.<br>3. Dividir entre el tiempo operativo. |
| Frecuencia | Cálculo por turno; análisis semanal. |
| Unidad | % |
| Fuente de datos | Fact_Produccion, Dim_Producto, Fact_Paros |
| Meta y semáforo | Verde ≥ 80 % · Amarillo 70 % a 80 % · Rojo < 70 % |
| Responsable | Administrador |

#### Indicador 1c · Calidad

| Campo | Detalle |
|---|---|
| Nombre | Calidad |
| Qué representa | Qué proporción de lo producido salió bueno. Mide las pérdidas por trenzas quemadas, crudas, deformes o descartadas. |
| Fórmula | Calidad = (Unidades producidas − Unidades defectuosas) ÷ Unidades producidas |
| Cómo se calcula | 1. Sumar las unidades producidas y las defectuosas del turno.<br>2. Restar para obtener las unidades buenas.<br>3. Dividir las buenas entre las producidas. |
| Frecuencia | Cálculo por turno; análisis semanal. |
| Unidad | % |
| Fuente de datos | Fact_Produccion |
| Meta y semáforo | Verde ≥ 95 % · Amarillo 90 % a 95 % · Rojo < 90 % |
| Responsable | Administrador |

---

### Indicador 2 · SLA de pedidos (OTIF: a tiempo y completos)

| Campo | Detalle |
|---|---|
| Nombre | SLA de pedidos (OTIF: a tiempo y completos) |
| Qué representa | El porcentaje de pedidos que se entregaron a la hora acordada o antes y con la cantidad completa. Mide el cumplimiento de la panadería con sus clientes de pedidos. |
| Fórmula | SLA = Pedidos a tiempo y completos ÷ Total de pedidos |
| Cómo se calcula | 1. Un pedido cumple si `fecha_hora_entrega ≤ fecha_hora_compromiso` Y `cantidad_entregada ≥ cantidad_pedida`.<br>2. Contar los pedidos que cumplen.<br>3. Dividir entre el total de pedidos del periodo. |
| Frecuencia | Cálculo diario; análisis semanal y mensual. |
| Unidad | % |
| Fuente de datos | Fact_Pedidos |
| Meta y semáforo | Verde ≥ 95 % · Amarillo 90 % a 95 % · Rojo < 90 % |
| Responsable | Administrador |

---

### Indicador 3 · % de producto no vendido

| Campo | Detalle |
|---|---|
| Nombre | % de producto no vendido |
| Qué representa | La proporción del pan trenza bueno que no se vendió el día en que se produjo. Mide la sobreproducción y el desperdicio, y orienta cuánto producir. |
| Fórmula | % no vendido = (Unidades buenas − Unidades vendidas) ÷ Unidades buenas |
| Cómo se calcula | 1. Unidades buenas del día = producidas − defectuosas (`Fact_Produccion`), sumando los dos turnos.<br>2. Unidades vendidas del día (`Fact_Ventas`), que incluyen mostrador y pedidos.<br>3. Restar y dividir entre las unidades buenas. |
| Frecuencia | Cálculo diario; análisis semanal y mensual. |
| Unidad | % |
| Fuente de datos | Fact_Produccion, Fact_Ventas |
| Meta y semáforo | Verde ≤ 10 % · Amarillo 10 % a 15 % · Rojo > 15 % |
| Responsable | Administrador |

---

### Indicador 4 · Productividad de mano de obra

| Campo | Detalle |
|---|---|
| Nombre | Productividad de mano de obra |
| Qué representa | Cuántas trenzas buenas se producen por cada hora trabajada por los operarios. Mide la eficiencia del trabajo de las personas en el proceso. |
| Fórmula | Productividad = Unidades buenas ÷ Horas-hombre trabajadas |
| Cómo se calcula | 1. Sumar las unidades buenas del turno.<br>2. Sumar las horas trabajadas de los operarios del turno (máximo 2 operarios).<br>3. Dividir unidades buenas entre horas-hombre. |
| Frecuencia | Cálculo por turno y por día; análisis mensual. |
| Unidad | Trenzas por hora-hombre |
| Fuente de datos | Fact_Produccion, Fact_ManoObra |
| Meta y semáforo | Verde ≥ línea base + 5 % · Amarillo entre la línea base y +5 % · Rojo < línea base |
| Responsable | Administrador |

---

## Fuentes

- El País. (2025). *¿Por qué el consumo de pan no crece en Colombia? Esto dicen los productores*. https://www.elpais.com.co/economia/por-que-el-consumo-de-pan-no-crece-en-colombia-esto-dicen-los-productores-0358.html
- Microsoft. (2024). *Important update to Microsoft Power BI pricing*. https://community.fabric.microsoft.com/t5/Power-BI-Updates-Blog/Important-update-to-Microsoft-Power-BI-pricing/ba-p/5174341
- *Ley 1581 de 2012, de protección de datos personales*. Congreso de la República de Colombia.
- *Ley 23 de 1982, sobre derechos de autor*. Congreso de la República de Colombia.
- International Organization for Standardization. (2010). *ISO 26000: Guía de responsabilidad social*.
- Naciones Unidas. (2015). *Objetivos de Desarrollo Sostenible: metas 8.2 y 12.3*.
