# Sprint Review y Sprint Retrospective · Sprint 2

**Tablero de Indicadores – Panadería San Nicolás**  
Proyecto de Aula 2026-2 · Gerencia de Proyectos · Ingeniería Industrial · Universidad de Medellín  
Metodología: Scrum · Repositorio: github.com/jpablovlsqz16/Proyecto-de-aula-gerencia-

**Base del documento.** Se elaboró a partir del contenido del repositorio: README, `Docs/Arquitectura.md`, `Docs/Decisiones_Tecnicas.md`, `Docs/Manual_Usuario.md`, `COMMIT.txt` y el historial de pull requests. El Sprint 2 corresponde a la **construcción de la aplicación web (HU-01 a HU-16)**, que reemplaza la versión rechazada de la primera entrega.

---

## PARTE 1. SPRINT REVIEW

### 1. Objetivo del sprint

Reconstruir el tablero de indicadores como una aplicación web con código propio, versionado en el repositorio, capaz de generar el tablero a partir de **cualquier libro de Excel** con la estructura de la plantilla `Base_Panaderia_Indicadores` (tablas Dim y Fact), y publicarla en GitHub Pages y en Google Apps Script.

### 2. Participantes

| Integrante | Rol Scrum |
| --- | --- |
| Ronal Alexander Álvarez Valencia (docente) | Product Owner |
| Juan Pablo | Scrum Master |
| María Camila | QA |
| Juan José | Desarrollador |
| Iván Santiago | Desarrollador |

### 3. Resumen ejecutivo

El sprint cerró con una aplicación funcional que calcula los cuatro indicadores del proceso de pan trenza (OEE del horno, SLA, % no vendido y productividad), los muestra con semáforo, hallazgos y gráficos, y funciona sin servidor, sin base de datos y sin conexión a internet. El cambio de arquitectura respondió a la observación del Product Owner sobre la primera entrega: la tecnología debía justificarse por costo, licencias, curva de aprendizaje, dependencia del proveedor y sostenibilidad. Se evaluaron cuatro alternativas con una matriz ponderada y se eligió la aplicación web estática (4,65 puntos) sobre Google Apps Script + Google Sheets (2,65), Python + Streamlit (3,70) y Power BI / Looker Studio (1,95). El cambio quedó registrado como **CC-01** en el control de cambios del informe.

### 4. Historias de usuario del sprint

| Historia | Entregable | Estado | Evidencia en el repositorio |
| --- | --- | --- | --- |
| HU-01 | Estructura base de la aplicación (Frontend y Backend) y justificación de la tecnología, escrita antes de la primera línea de código | Terminada | `Docs/Decisiones_Tecnicas.md`, `Frontend/index.html`, `Backend/` |
| HU-02 | Plantilla vacía de Excel con las tablas Dim y Fact | Terminada | `Frontend/datos/` |
| HU-03 | Simulación de Montecarlo de los datos de septiembre de 2026, con autorización del docente | Terminada | `Simulacion/simular_datos.py`, `Docs/Supuestos_Simulacion.md` |
| HU-04 | Lectura del libro de Excel con SheetJS y conversión de textos, números con coma decimal y fechas (incluido el número de serie de Excel) | Terminada | `Frontend/js/lectura.js`, `Frontend/vendor/` |
| HU-05 | Reconocimiento de tablas por sus columnas, validación de filas y unión de hechos con dimensiones | Terminada | `Frontend/js/modelo.js` |
| HU-06 a HU-11 | Registro por turno (tiempo programado, operativo e ideal) y cálculo de disponibilidad, rendimiento, calidad, OEE, SLA, % no vendido, productividad, consolidados y semáforo | Terminada | `Frontend/js/indicadores.js` |
| HU-12 | Gráficos con Chart.js: OEE por día, cascada de tiempo del horno, Pareto de paros, SLA, % no vendido, productividad y OEE por turno | Terminada | `Frontend/js/app.js`, `Frontend/vendor/` |
| HU-13 y HU-14 | Hallazgos automáticos, filtros por fecha y turno, metas editables, exportación a CSV e impresión | Terminada | `Frontend/js/app.js`, `Docs/Manual_Usuario.md` |
| HU-15 | Prueba con un archivo distinto: otro mes simulado (octubre) y la base OEE del curso | Terminada | `Simulacion/`, `Docs/Decisiones_Tecnicas.md` (riesgo R1) |
| HU-16 | Publicación como aplicación web de Google Apps Script | Terminada | `Backend/Code.gs`, `Backend/appsscript.json`, `Backend/construir_index.py` |

Historias sin terminar: **ninguna**. Queda una acción técnica pendiente fuera de las historias (actualizar SheetJS), descrita en la sección 9.

### 5. Demostración del incremento

Flujo mostrado a los interesados:

1. Abrir la aplicación en GitHub Pages, en Google Apps Script o directamente con `Frontend/index.html` sin internet.
2. En **Cargar datos**, descargar la plantilla de Excel y diligenciarla, o usar **Usar datos de ejemplo** (septiembre de 2026, simulados).
3. Arrastrar el libro a la aplicación. La aplicación reconoce las tablas por sus columnas, valida cada fila y lista las rechazadas con hoja, fila y motivo.
4. Leer el tablero: tarjetas con semáforo, frases de hallazgos y gráficos.
5. Filtrar por fechas y turno, cambiar las metas y restaurar los valores de las fichas técnicas.
6. Exportar a CSV o imprimir.
7. Cargar un archivo distinto (octubre, o la base OEE del curso) para comprobar que el tablero se regenera sin cambiar el código.

### 6. Indicadores entregados

| Dimensión | Indicador | Fórmula | Meta (verde) |
| --- | --- | --- | --- |
| Equipo | OEE del horno | Disponibilidad × Rendimiento × Calidad | ≥ 65 % |
| Cliente | SLA (OTIF) | Pedidos a tiempo y completos ÷ Total de pedidos | ≥ 95 % |
| Desperdicio | % no vendido | (Unidades buenas − Vendidas) ÷ Unidades buenas | ≤ 10 % |
| Personas | Productividad | Unidades buenas ÷ Horas-hombre | ≥ línea base + 5 % |

Reglas de cálculo acordadas con el Product Owner:

- Los consolidados **suman primero tiempos y unidades**; no promedian porcentajes, para que un turno corto no pese igual que uno largo.
- Tiempo programado = duración del turno − descanso − paros con `excluir_tiempo_programado = S`.
- Tiempo operativo = tiempo programado − paros no planeados.
- Tiempo ideal = Σ unidades × (tiempo de horneado ÷ unidades por tanda).
- El % no vendido se calcula solo por día, porque las ventas se registran por día. Con filtro de turno muestra N/D.
- Un motivo de paro fuera del catálogo no cuenta y se avisa para que el usuario lo agregue a `Dim_MotivoParo`.

### 7. Calidad y Definición de Terminado

| Criterio | Cumplimiento |
| --- | --- |
| El código fuente existe solo como archivos del repositorio, bajo control de versiones | Cumple. `Backend/Index.html` se genera desde `Frontend/` con `construir_index.py` y no se edita a mano |
| Pruebas automáticas por historia | Cumple. `npm test` (Node.js 18 o superior, sin dependencias) con un archivo de pruebas por historia de HU-04 a HU-15 |
| Lógica separada de la interfaz | Cumple. `lectura.js`, `modelo.js` e `indicadores.js` son funciones puras que se prueban sin abrir el navegador |
| Funciona con un archivo distinto al de desarrollo | Cumple. Probado con la plantilla de la panadería, otro mes simulado y la base OEE del curso |
| Funciona sin internet | Cumple. Chart.js 4.4.1 y SheetJS 0.18.5 están incluidas en `Frontend/vendor/` |
| Sin Google Sheets en el flujo de datos | Cumple. Los datos se procesan en el navegador y solo se guardan en `localStorage` |
| Documentación al día | Cumple. Arquitectura, decisiones técnicas, manual de usuario, supuestos de simulación y declaración de uso ético de IA |
| QA antes de «Terminado» | Cumple. María Camila validó cada historia antes de cerrarla |

### 8. Métricas del sprint

| Métrica | Valor |
| --- | --- |
| Historias de usuario planeadas | 16 (HU-01 a HU-16) |
| Historias terminadas | 16 |
| Historias no terminadas | 0 |
| Commits en `main` (acumulado del proyecto) | 118 |
| Pull requests cerrados | 52 |
| Pull requests abiertos al cierre | 0 |
| Indicadores implementados | 4 |
| Tablas del modelo de datos | 9 (5 de hechos y 4 dimensiones) |
| Licencias de las librerías | MIT (Chart.js) y Apache 2.0 (SheetJS) |
| Costo de operación | $0 |

### 9. Riesgos y pendientes al cierre

| Riesgo o pendiente | Prob. | Impacto | Respuesta |
| --- | --- | --- | --- |
| SheetJS 0.18.5 tiene vulnerabilidades conocidas al leer archivos manipulados (CVE-2023-30533 y CVE-2024-22363) | Baja | Medio | El archivo lo elige el propio usuario y se procesa solo en su navegador. **Pendiente:** reemplazar `Frontend/vendor/xlsx.full.min.js` por la 0.20.3 y correr `npm test` |
| El archivo del docente usa encabezados no previstos | Media | Alto | Reconocimiento de tablas por sinónimos en español e inglés |
| Sin internet el día de la demostración | Media | Alto | Modo local con `Frontend/index.html` |
| Los datos guardados en el navegador se pierden al borrar la caché | Media | Bajo | Basta volver a cargar el archivo fuente |
| El `Index.html` de Apps Script queda desactualizado si no se regenera | Media | Medio | Regenerarlo con `construir_index.py` antes de cada publicación |

### 10. Retroalimentación del Product Owner y ajustes al backlog

- **Observación recibida:** la elección de Google Apps Script y Google Sheets debía justificarse por costo, licencias, curva de aprendizaje, dependencia del proveedor y sostenibilidad. **Respuesta del equipo:** se redactó `Decisiones_Tecnicas.md` con la matriz de alternativas y se registró el cambio como CC-01.
- **Ajuste de planificación:** se unificó la numeración. Los productos de gestión pasaron a E-01…E-26 y las historias de la aplicación a HU-01…HU-16. Se corrigieron `Sprint_Planning.md`, `Desarrollo_Primera_Entrega.md`, `Historias_Usuario_Segunda_Entrega.md` y `Registro_Commits.md`, y se agregó el diagrama de arquitectura.
- **Backlog para el siguiente sprint:** actualizar SheetJS, alinear el README con la arquitectura vigente y cerrar la documentación de la sustentación.

---

## PARTE 2. SPRINT RETROSPECTIVE

**Formato:** Qué salió bien, qué no salió bien, qué aprendimos y Start / Stop / Continue.  
**Facilita:** Juan Pablo (Scrum Master).  
**Participan:** todo el equipo Scrum.

### 1. Qué salió bien

- **La decisión tecnológica quedó argumentada.** La matriz ponderada con cinco criterios y pesos explícitos convirtió una observación del Product Owner en una decisión defendible.
- **El código ahora es del equipo y no de una cuenta.** Todo vive en el repositorio y cualquiera lo clona y lo abre. Esto elimina la dependencia de la cuenta de Google de un integrante.
- **Flujo de trabajo disciplinado.** El historial muestra 118 commits y 52 pull requests cerrados, ninguno abierto. Se trabajó con ramas, pull request y merge, como describe `COMMIT.txt`.
- **Arquitectura testeable.** Separar funciones puras de la interfaz permitió probar la lógica con Node.js, con un archivo de pruebas por historia.
- **Funciona en cualquier escenario de demostración.** Hay tres vías de acceso (GitHub Pages, Apps Script y modo local sin internet) y se probó con archivos distintos al de desarrollo.
- **Decisiones de cálculo trazables.** Consolidar sumando tiempos y unidades, y no promediando porcentajes, quedó documentado con su razón.
- **Documentación completa.** Arquitectura, decisiones técnicas, manual, supuestos de simulación y declaración de uso ético de IA.
- **Transparencia con los datos.** Se aclaró que los datos son simulados con autorización del docente y se documentaron los supuestos.

### 2. Qué no salió bien

- **El código de la primera entrega nunca se subió al repositorio.** Las carpetas `Frontend/` y `Backend/` quedaron vacías. Fue un problema de proceso, no de tecnología, y obligó a rehacer el trabajo.
- **La numeración de historias se mezcló.** Las historias de gestión y las de la aplicación compartían el prefijo HU, y hubo que corregir cuatro documentos (el Paso 0 de `COMMIT.txt`).
- **La documentación se desfasa del código.** El README anterior todavía describía Google Sheets como base de datos, cuando la arquitectura vigente no lo usa.
- **Una librería quedó con vulnerabilidades conocidas.** SheetJS 0.18.5 sigue en `vendor/` y la actualización a la 0.20.3 está pendiente.
- **Publicar en Apps Script depende de una sola cuenta.** Aunque la app ya no depende de Google para funcionar, el script sigue ligado a la cuenta de quien lo creó.
- **El `Index.html` generado puede quedar viejo.** Depende de que alguien recuerde correr `construir_index.py`.

### 3. Qué aprendimos

- Con control de versiones, el historial de commits es la evidencia del trabajo, y no subir código equivale a no haberlo hecho.
- Justificar la tecnología antes de programar evita rehacer: la guía evalúa la justificación, no la sofisticación.
- Una arquitectura de cliente puro bajó el costo, el riesgo operativo y la curva de aprendizaje al mismo tiempo.
- La numeración y los nombres de los productos se acuerdan en la planeación, porque cambiarlos después cuesta más que definirlos bien.
- Reconocer las tablas por sus columnas y no por el nombre de la hoja protege la demostración con un archivo desconocido.

### 4. Start / Stop / Continue

| Empezar (Start) | Dejar de hacer (Stop) | Continuar (Continue) |
| --- | --- | --- |
| Actualizar las dependencias al cerrar cada sprint | Dejar código fuera del repositorio | Un pull request pequeño por historia |
| Revisar la documentación contra el código antes de cerrar una historia | Mezclar prefijos entre historias de gestión y de la aplicación | Pruebas automáticas por historia |
| Regenerar `Index.html` como paso fijo de la publicación | Depender de una sola cuenta para publicar | Revisión de QA antes de «Terminado» |
| Dar acceso de editor a más de un integrante en Apps Script | Decidir la tecnología después de empezar a programar | Documentar cada decisión técnica con su justificación |
| Probar cada entrega con un archivo distinto al de desarrollo | Dejar acciones de seguridad sin responsable | Datos simulados con supuestos documentados |

### 5. Acciones de mejora para el Sprint 3

| # | Acción | Responsable | Cómo se verifica |
| --- | --- | --- | --- |
| 1 | Reemplazar `Frontend/vendor/xlsx.full.min.js` por SheetJS 0.20.3 desde cdn.sheetjs.com y correr `npm test` | Juan José | Pruebas en verde y versión nueva en `Decisiones_Tecnicas.md` |
| 2 | Alinear el README con la arquitectura vigente (sin Google Sheets, con GitHub Pages y modo local) | Iván Santiago | README igual al de la rama `main` y sin referencias a Sheets |
| 3 | Agregar a la Definición de Terminado el punto «documentación sincronizada con el código» | María Camila | Lista de verificación de QA actualizada |
| 4 | Incluir en la lista de publicación el paso de regenerar `Backend/Index.html` | Juan Pablo | Paso escrito en el procedimiento y confirmado en cada publicación |
| 5 | Dar acceso de editor del proyecto de Apps Script a todo el equipo | Juan Pablo | Todos los integrantes pueden abrir el script |
| 6 | Revisar el uso de pull requests y ramas para que todo cambio pase por QA antes del merge | María Camila | Cero cambios directos a `main` en el sprint |

### 6. Compromisos del equipo

- Todo el código, los datos de prueba y la documentación se suben al repositorio el mismo día en que se producen.
- Ninguna historia se marca como terminada sin pruebas, revisión de QA y documentación al día.
- Las decisiones técnicas se escriben con su justificación antes de implementarse.
- La retrospectiva siguiente revisará si las seis acciones anteriores se cumplieron.

### 7. Conclusión

El Sprint 2 resolvió el problema de fondo de la primera entrega: ahora el producto es el repositorio, se genera con cualquier archivo de datos y se justifica con criterios medibles. Los puntos débiles que quedan son de mantenimiento y de proceso (una librería por actualizar, documentación que se desfasa y una publicación ligada a una sola cuenta), y todos tienen una acción con responsable para el siguiente sprint.
