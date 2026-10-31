# HU-22 · Registrar el seguimiento de la ejecución

Tablero de Indicadores · Panadería San Nicolás (pan trenza) · Scrum Master: Juan Pablo

Proyecto de Aula 2026-2 · Gerencia de Proyectos · Segunda entrega · Corte de datos: 31 de octubre de 2026, 00:31 (hora de Colombia). En el repositorio esta historia figura como E-22.

---

## 1. Sprints realizados

| **Sprint** | **Ejecutado** | **Objetivo** | **Resultado** |
|---|---|---|---|
| **Sprint 0** | 24 – 27 oct | Corregir la primera entrega y dejar listos el repositorio, el planning y la numeración de las historias. | Repositorio, carpetas, README y planning integrados el 24 de octubre. Numeración única (E-01 a E-26 de gestión; HU-01 a HU-16 de la app) integrada en el PR #4 el 27 oct 00:40. |
| **Sprint 1** | 26 – 29 oct | Modelo híbrido, modelo de negocio y financiación de la segunda entrega, y la aplicación hasta el prototipo v0 con SLA y % no vendido. | **12 de 13 historias y 53 de 56 puntos (94,6 %).** El prototipo v0 (OEE del horno) se integró el 29 oct 22:29. La historia restante pasó al Sprint 2. |
| **Sprint 2** | 30 – 31 oct | Cerrar la aplicación (prototipo final probado con un archivo distinto) y completar seguimiento, pruebas, validación, cierre y sustentación. | Al corte: integradas las 9 historias HU-08 a HU-16 de la app; el prototipo final (PR #46) quedó el 31 oct 00:31. Siguen HU-22 a HU-26: [completar al cierre]. |

---

## 2. Cronograma planeado frente a ejecutado

| **Sprint** | **Plan original** | **Plan ajustado** | **Ejecutado** | **Desviación** |
|---|---|---|---|---|
| Sprint 0 | 24 – 25 oct | — | 24 oct – 27 oct 00:40 (PR #4) | +1 día frente al plan |
| Sprint 1 | 26 – 27 oct | 26 – 29 oct | 26 – 29 oct (último cierre: 29 oct 23:09, PR #33) | +2 días frente al original; 0 frente al ajustado |
| Sprint 2 | 28 – 29 oct | 30 – 31 oct | 30 – 31 oct (app cerrada el 31 oct 00:31) | +2 días frente al original; 0 frente al ajustado |

Las desviaciones de los Sprints 1 y 2 vienen del cambio de fechas registrado en CC-01 (sección 5). El detalle por historia está en la sección 3.

---

## 3. Tiempo estimado frente al real

**Estimado:** el presupuesto del business case (240 h) repartido en los 170 puntos de todo el backlog da **1,41 h por punto** (supuesto del equipo). **Real:** el equipo no registró horas durante el proyecto; cada integrante reporta un promedio de **2 a 3 horas por día, sin variar entre sprints**. Se usa el punto medio (2,5 h) × 4 integrantes × los días del sprint, y se reparte entre las historias del sprint según sus puntos. La diferencia es real − estimado.

| **Sprint** | **Días** | **Horas reales (4 × 2,5 h × días)** | **Rango (2 a 3 h por día)** | **Horas estimadas** | **Diferencia** | **%** |
|---|---|---|---|---|---|---|
| Sprint 1 | 4 | 40,0 h | 32 – 48 h | 79,1 h | −39,1 h | −49 % |
| Sprint 2 | 2 | 20,0 h | 16 – 24 h | 69,2 h | −49,2 h | −71 % |
| **Total** | **6** | **60,0 h** | **48 – 72 h** | **148,2 h** | **−88,2 h** | **−60 %** |

Por historia (horas reales asignadas por puntos; el Sprint 2 incluye también el tiempo de HU-22 a HU-26, que aún no están integradas):

| **Historia** | **Sp.** | **Pts** | **PR · commit** | **Integrada** | **H. est.** | **H. real** | **Dif. (h)** |
|---|---|---|---|---|---|---|---|
| **Sprint 1 · segunda entrega (documentos)** | | | | | | | |
| HU-17 | 1 | 5 | #21 · fdd04b3 | 28 oct 23:38 | 7,1 | 3,6 | −3,5 |
| HU-18 | 1 | 3 | #22 · 09d1b71 | 29 oct 00:12 | 4,2 | 2,1 | −2,1 |
| HU-19 | 1 | 8 | #24 · 5fd8fde | 29 oct 00:39 | 11,3 | 5,7 | −5,6 |
| HU-20 | 1 | 3 | #25 · 43679bd | 29 oct 00:45 | 4,2 | 2,1 | −2,1 |
| HU-21 | 1 | 5 | #34 · de872cd | 29 oct 23:04 | 7,1 | 3,6 | −3,5 |
| **Sprint 1 · aplicación** | | | | | | | |
| HU-01 (app) | 1 | 3 | #15 · 4da40cb | 29 oct 12:17 | 4,2 | 2,1 | −2,1 |
| HU-02 (app) | 1 | 2 | #27 · 7928c50 | 29 oct 14:55 | 2,8 | 1,4 | −1,4 |
| HU-03 (app) | 1 | 5 | #28 · 3b39f73 | 29 oct 18:41 | 7,1 | 3,6 | −3,5 |
| HU-04 (app) | 1 | 3 | #29 · 90ecb7a | 29 oct 20:29 | 4,2 | 2,1 | −2,1 |
| HU-05 (app) | 1 | 5 | #31 · a2fd083 | 29 oct 22:08 | 7,1 | 3,6 | −3,5 |
| HU-06 (app) | 1 | 8 | #32 · 7f85926 | 29 oct 22:29 | 11,3 | 5,7 | −5,6 |
| HU-07 (app) | 1 | 3 | #33 · 5af4a7e | 29 oct 23:09 | 4,2 | 2,1 | −2,1 |
| HU-08 (app) † | 1 | 3 | #35 · 4618c05 | 30 oct 19:33 | 4,2 | 2,1 | −2,1 |
| **Sprint 2 · aplicación** | | | | | | | |
| HU-09 (app) | 2 | 3 | #38 · 8a8ea79 | 30 oct 20:08 | 4,2 | 1,2 | −3,0 |
| HU-10 (app) | 2 | 3 | #39 · f157156 | 30 oct 20:17 | 4,2 | 1,2 | −3,0 |
| HU-11 (app) | 2 | 3 | #40 · f83f718 | 30 oct 20:55 | 4,2 | 1,2 | −3,0 |
| HU-12 (app) | 2 | 5 | #41 · f14642f | 30 oct 21:48 | 7,1 | 2,0 | −5,0 |
| HU-13 (app) | 2 | 3 | #42 · 455c6ac | 30 oct 22:08 | 4,2 | 1,2 | −3,0 |
| HU-14 (app) | 2 | 2 | #43 · 51f4770 | 30 oct 23:30 | 2,8 | 0,8 | −2,0 |
| HU-15 (app) | 2 | 5 | #45 · d58153a | 31 oct 00:06 | 7,1 | 2,0 | −5,0 |
| HU-16 (app) | 2 | 3 | #46 · b1cf236 | 31 oct 00:31 | 4,2 | 1,2 | −3,0 |
| **Total integrado** | | **83** | | | **117,2** | **51,0** | **−66,2** |

*† Planeada para el Sprint 1; según el repositorio se integró el 30 de octubre, ya en el Sprint 2. Cada commit se abre en github.com/jpablovlsqz16/Proyecto-de-aula-gerencia-/commit/\<hash\>.*

---

## 4. Valor ganado

**Línea base (supuesto):** el presupuesto del proyecto es **$4.800.000** (240 h × $20.000, costo de oportunidad del business case), repartido en proporción a los puntos: **$28.235 por punto**. La fase de ejecución (Sprints 1 y 2, 105 puntos) tiene un BAC de **$2.964.706** (148,2 h). El costo real (AC) son las horas reales de la sección 3 × $20.000.

| **Medida** | **Fórmula** | **Corte 1 · cierre Sprint 1 (29 oct)** | **Corte 2 · cierre Sprint 2 (31 oct)** |
|---|---|---|---|
| **PV (planeado)** | Puntos planeados × valor por punto | 56 pts → $1.581.176 | 105 pts → $2.964.706 |
| **EV (ganado)** | Puntos terminados × valor por punto | 53 pts → $1.496.471 | [completar al cierre] |
| **AC (real)** | Horas reales × $20.000 | 40 h → $800.000 | 60 h → $1.200.000 (si se mantiene el ritmo hasta el 31 oct) |
| **SV** | EV − PV | −$84.706 | [completar al cierre] |
| **SPI** | EV ÷ PV | 0,95 | [completar al cierre] |
| **CV** | EV − AC | +$696.471 | [completar al cierre] |
| **CPI** | EV ÷ AC | 1,87 (rango 1,56 a 2,34) | [completar al cierre] |
| **EAC** | BAC ÷ CPI | $1.584.906 (indicativo) | [completar al cierre] |

**Plazo (corte 1):** SPI = 0,95. A la fecha se completó el 94,6 % del trabajo planeado; el atraso equivale a 3 puntos (una historia, $84.706) y se recuperó en el Sprint 2. **Costo (corte 1):** CPI = 1,87. Cada punto ganado costó menos horas de las presupuestadas (0,75 h reales frente a 1,41 h), y el EAC proyectado queda por debajo del BAC. Dos advertencias: las horas son un promedio reportado por el equipo y no un registro, y el presupuesto de 240 h del business case fue un supuesto conservador. Por eso el CPI debe leerse como una tendencia, no como una medición exacta.

---

## 5. Solicitudes de cambio

| **N.°** | **Fecha** | **Descripción** | **Impacto** | **Decisión** |
|---|---|---|---|---|
| CC-01 | [completar] (documentado el 30 oct 13:34, PR #36) | Cambio de fechas a solicitud del equipo: Sprint 1 del 26 al 29 de octubre y Sprint 2 del 30 al 31. | Alcance sin cambio. Sprint 1 pasa de 2 a 4 días y Sprint 2 se desplaza 2 días. | [completar: decisión del Product Owner] |
| CC-02 | 29 oct (Sprint Review) | Una historia del Sprint 1 pasa al Sprint 2 para cerrarse: la Review nombra la HU-07 (pendiente de aprobación); el repositorio muestra la HU-08 integrada el 30 oct. [confirmar cuál] | El Sprint 2 sube de 49 a 52 puntos (+3). | Acordado en la Review [confirmar con el Product Owner] |
| CC-03 | 28 oct 16:50 | Se revierten los PR #5 a #9 (HU-01 a HU-05 de la app, integrados el 27 oct) y las historias se rehacen. | Retrabajo de 18 puntos; las cinco se integran de nuevo el 29 oct entre las 12:17 y las 22:08. | [completar: quién lo decidió y por qué] |
| CC-04 | 27 oct 00:40 | Numeración única: gestión E-01 a E-26 y aplicación HU-01 a HU-16 (PR #4). | Sin cambio de alcance; se renumeran los documentos. | Integrado en main (PR #4) |

---

## 6. Evidencia del repositorio

- **Repositorio:** https://github.com/jpablovlsqz16/Proyecto-de-aula-gerencia-
- **Actividad:** 109 commits y 42 pull requests integrados entre el 24 de octubre (17:36) y el 31 de octubre (00:31).
- **Registro completo:** Docs/Registro_Commits.md (hash, autor, fecha, mensaje y archivos de cada commit). Cada historia de la sección 3 enlaza con su commit de integración.
- **Pruebas automáticas:** npm test ejecutado sobre el repositorio, 33 de 33 pruebas aprobadas.
- **Documento resuelto:** este archivo, Docs/HU-22_Seguimiento_Ejecucion.md.

