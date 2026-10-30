# Sprint Planning · Sprints 1 y 2

Tablero de Indicadores · Panadería San Nicolás (pan trenza)

Proyecto de Aula 2026-2 · Gerencia de Proyectos · Metodología Scrum · Segunda entrega

**Product Owner:** Ronal Alexander Álvarez Valencia · **Scrum Master:** Juan Pablo · **QA:** María Camila · **Desarrolladores:** Juan José e Iván Santiago. Cada sprint toma historias de dos listas: las de la **segunda entrega** (HU-17 a HU-26) y las de la **construcción de la aplicación** (HU-01 a HU-16 de ese documento, marcadas «app» para no confundirlas).

---

## 1. Cambio de fechas de los sprints

| **Sprint** | **Fechas originales** | **Fechas nuevas** | **Cambio** |
|---|---|---|---|
| **Sprint 1** | lun 26 – mar 27 oct (2 días) | lun 26 – jue 29 oct (4 días) | Se amplía 2 días |
| **Sprint 2** | mié 28 – jue 29 oct (2 días) | vie 30 – sáb 31 oct (2 días) | Se desplaza 2 días |

El alcance de cada sprint no cambia: Sprint 1 conserva HU-17 a HU-21 y HU-01 a HU-08 (app); Sprint 2 conserva HU-22 a HU-26 y HU-09 a HU-16 (app). Solo se mueven las fechas. El Sprint 0 (24 y 25 de octubre) no se modifica.

### Motivo

El equipo solicitó el cambio porque dos días no alcanzaban para la carga del Sprint 1: reunía **56 puntos** (24 de la segunda entrega y 32 de la aplicación), es decir **28 puntos por día**. Con cuatro días baja a **14 puntos por día**. Tres condiciones del proyecto respaldan la solicitud:

- **Las historias de la aplicación van en cadena.** Cada una se integra a main por Pull Request antes de empezar la siguiente, así que HU-01 a HU-08 (32 puntos) no se pueden repartir en paralelo.
- **QA es el cuello de botella.** Cada historia necesita revisión de QA para pasar a «Terminado». María Camila revisa las historias de la aplicación y además es responsable de 16 puntos del Sprint 1 (HU-18, HU-20, HU-21 y HU-03 app).
- **La definición de terminado pide más que el código:** el documento resuelto subido, el commit en el repositorio y la aceptación en la Sprint Review. Eso suma trabajo por historia que el plan de dos días no consideró.

### Registro del cambio

| Campo | Detalle |
|---|---|
| **Solicitado por** | Equipo de desarrollo |
| **Fecha de la solicitud** | [completar] |
| **Impacto en el cronograma** | Sprint 1 pasa de 2 a 4 días. Sprint 2 se desplaza dos días, mantiene su duración y termina el sábado 31 de octubre. |
| **Decisión del Product Owner** | [completar] |

---

## 2. Definición de terminado y eventos

Una historia está terminada cuando cumple sus criterios de aceptación, QA la revisó, el documento resuelto quedó subido (o pasan las pruebas automáticas, en las de la aplicación), los cambios están en el repositorio por Pull Request, la tarjeta está en «Terminado» en Trello y fue aceptada en la Sprint Review. Cada sprint tiene Sprint Planning (este documento), Daily Scrum, Sprint Review con el Product Owner el último día y retrospectiva obligatoria.

---

## 3. Sprint Planning · Sprint 1

| Campo | Detalle |
|---|---|
| **Fechas** | Lunes 26 a jueves 29 de octubre de 2026 (4 días) |
| **Objetivo del sprint** | Dejar definidos el modelo híbrido, el modelo de negocio y la financiación de la segunda entrega, y tener la aplicación hasta el prototipo v0 (OEE del horno) con el SLA de pedidos y el % de producto no vendido. |
| **Puntos comprometidos** | **56** (24 de la segunda entrega + 32 de la aplicación) |
| **Entrega** | Las historias se entregan entre el 26 y el 29 de octubre, sin día fijo por historia. |
| **Sprint Review y retrospectiva** | Jueves 29 de octubre, con el Product Owner. La retrospectiva es obligatoria. |

### Historias seleccionadas

| **ID** | **Historia** | **Responsable** | **Prioridad** | **Pts** |
|---|---|---|---|---|
| **Segunda entrega (documentos)** | | | | |
| HU-17 | Definir el modelo híbrido | Juan Pablo | Alta | 5 |
| HU-18 | Priorizar con MoSCoW y gestionar el flujo con Kanban | María Camila | Media | 3 |
| HU-19 | Construir el CANVAS ampliado | Juan Pablo | Alta | 8 |
| HU-20 | Realizar el análisis PESTEL | María Camila | Media | 3 |
| HU-21 | Evaluar opciones de financiación | María Camila | Media | 5 |
| **Construcción de la aplicación** | | | | |
| HU-01 (app) | Crear la estructura y la arquitectura de la aplicación | Iván Santiago | Alta | 3 |
| HU-02 (app) | Diseñar la plantilla de Excel y el diccionario de datos | Juan José | Alta | 2 |
| HU-03 (app) | Simular un mes de datos del proceso | María Camila | Alta | 5 |
| HU-04 (app) | Cargar el libro de Excel | Juan José | Alta | 3 |
| HU-05 (app) | Reconocer las tablas y validar los datos | Iván Santiago | Alta | 5 |
| HU-06 (app) | Ver el OEE del horno (prototipo v0) | Iván Santiago | Alta | 8 |
| HU-07 (app) | Medir el SLA de pedidos (OTIF) | Juan José | Alta | 3 |
| HU-08 (app) | Medir el % de producto no vendido | Juan José | Alta | 3 |
| | **Total del Sprint 1** | | | **56** |

**Carga por integrante:** Juan Pablo 13 pts · María Camila 16 pts (HU-18, HU-20, HU-21 y HU-03 app) · Juan José 11 pts · Iván Santiago 16 pts.

### Riesgos del sprint

- HU-06 (8 puntos) es la más grande y de ella dependen HU-07 y HU-08.
- La revisión de QA recae en María Camila: las historias deben llegar a revisión de forma escalonada, no todas al final.

---

## 4. Sprint Planning · Sprint 2

| Campo | Detalle |
|---|---|
| **Fechas** | Viernes 30 y sábado 31 de octubre de 2026 (2 días) |
| **Objetivo del sprint** | Cerrar la aplicación (prototipo final publicado y probado con un archivo distinto) y completar el seguimiento de la ejecución, las pruebas, la validación, el cierre y la sustentación de la segunda entrega. |
| **Puntos comprometidos** | **49** (22 de la segunda entrega + 27 de la aplicación) |
| **Entrega** | Las historias se entregan entre el 30 y el 31 de octubre, sin día fijo por historia. |
| **Sprint Review y retrospectiva** | Sábado 31 de octubre, con el Product Owner. La retrospectiva es obligatoria. |

### Historias seleccionadas

| **ID** | **Historia** | **Responsable** | **Prioridad** | **Pts** |
|---|---|---|---|---|
| **Segunda entrega (documentos)** | | | | |
| HU-22 | Registrar el seguimiento de la ejecución | Juan Pablo | Alta | 8 |
| HU-23 | Ejecutar el plan de pruebas | María Camila | Alta | 5 |
| HU-24 | Validar la aplicación con el usuario | María Camila | Alta | 3 |
| HU-25 | Registrar resultados y cierre | María Camila | Media | 3 |
| HU-26 | Preparar la sustentación y la demostración | Juan José | Alta | 3 |
| **Construcción de la aplicación** | | | | |
| HU-09 (app) | Medir la productividad de mano de obra | Juan José | Media | 3 |
| HU-10 (app) | Ver el semáforo y ajustar las metas | Juan José | Alta | 3 |
| HU-11 (app) | Filtrar por fechas, turno y equipo | Iván Santiago | Media | 3 |
| HU-12 (app) | Ver los gráficos del tablero | Iván Santiago | Media | 5 |
| HU-13 (app) | Leer los hallazgos automáticos | Juan José | Media | 3 |
| HU-14 (app) | Exportar e imprimir el tablero | Juan José | Baja | 2 |
| HU-15 (app) | Probar la aplicación con un archivo distinto | María Camila | Alta | 5 |
| HU-16 (app) | Publicar el prototipo final | Iván Santiago | Alta | 3 |
| | **Total del Sprint 2** | | | **49** |

**Carga por integrante:** Juan Pablo 8 pts · María Camila 16 pts (HU-23, HU-24, HU-25 y HU-15 app) · Juan José 14 pts · Iván Santiago 11 pts.

### Riesgos del sprint

- **Carga alta en poco tiempo.** El Sprint 2 sigue siendo de 2 días con 49 puntos, unos **24,5 por día**, casi el doble del Sprint 1. Si hay que recortar, se hace por prioridad: primero HU-14 (Baja) y luego las de prioridad Media (HU-09, HU-11, HU-12, HU-13 y HU-25).
- HU-15 (prueba con un archivo distinto) y HU-16 (publicación) dependen de que HU-09 a HU-14 estén integradas.
- Cualquier historia del Sprint 1 que no cierre el jueves 29 pasa a este sprint y suma a la carga.
