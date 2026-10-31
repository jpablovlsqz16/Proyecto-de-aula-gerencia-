# HU-25 · Registrar Resultados y Cierre

**Proyecto:** Tablero de Indicadores · Panadería San Nicolás (Pan Trenza)  
**Responsable:** María Camila Tamayo Cuesta · QA / Equipo Scrum  
**Proyecto de Aula 2026-2:** Gerencia de Proyectos · Segunda Entrega  
**Fecha de Corte:** 31 de octubre de 2026 · En el backlog figura como E-25  

---

## 1. Beneficio Frente a la Línea Base (CA1)

Los beneficios del proyecto están alineados con el *Business Case* inicial (E-08). Al ser datos de simulación autorizados por el docente, el beneficio reportado corresponde a la estimación económica proyectada, la cual será contrastada mes a mes a partir del inicio de la operación real:

| Beneficio | Indicador | Línea Base | Meta (Verde) | Responsable / Medición | Valor de Prueba (Simulado) |
|---|---|:---:|:---:|:---:|:---:|
| **Menos pan no vendido** | % producto no vendido | 12 % (supuesto) | ≤ 10 % | Administrador · Mensual | 5,8 % |
| **Mejor cumplimiento de pedidos** | SLA (OTIF) | Primer mes | ≥ 95 % | Administrador · Mensual | 90,6 % |
| **Mejor uso del horno** | OEE del horno | Primer mes | ≥ 65 % | Administrador · Mensual | 64,6 % |
| **Mayor productividad laboral** | Unidades buenas / h-h | Primer mes | Línea base + 5 % | Administrador · Mensual | 7,92 trenzas/h-h |

### Cálculo Financiero del Beneficio Principal (Reducción de Merma de Pan Trenza)

| Concepto Económico | Valor Estimado |
|---|---|
| **Producción mensual estimada de pan trenza** | ≈ 5.760 trenzas (262 unidades/día × 22 días laborables) |
| **Reducción de no vendido (de línea base 12% a meta 9%)** | 3 puntos porcentuales ≈ **173 trenzas ahorradas al mes** |
| **Costo unitario de producción por trenza** | \$2.500 COP |
| **Ahorro mensual bruto estimado** | 173 trenzas × \$2.500 ≈ **\$432.000 COP/mes** |
| **Costo de soporte y mantenimiento técnico** | 2 horas/mes × \$20.000 = **−\$40.000 COP/mes** |
| **Flujo neto mensual para la panadería** | **+\$392.000 COP/mes** |
| **Retorno de la inversión (Inversión inicial: \$4.800.000)** | **Recuperación (Payback) en ≈ 13 meses**<br>**VPN a 24 meses: ≈ +\$3.578.000 COP** (tasa de descuento 12% E.A.) |

> **Fórmula para auditoría mensual de beneficio real:**  
> $\text{Ahorro Real} = (12\% - \% \text{ No Vendido Medido}) \times \text{Trenzas Buenas Producidas} \times \$2.500$

---

## 2. Lecciones Aprendidas (CA2)

Se consolidaron 6 lecciones aprendidas clave derivadas de la ejecución de los Sprints 0, 1 y 2:

| N.° | Qué pasó (Situación real) | Qué aprendimos | Qué haremos la próxima vez |
|:---:|---|---|---|
| **1** | No se registraron las horas diarias durante la ejecución; en la HU-22 se debió usar un promedio reportado (2 a 3 h/día). | La falta de bitácora horaria dificulta la precisión del cálculo de CPI y horas reales por historia. | Implementar un registro de horas individual diario desde el Sprint 0. |
| **2** | Se planificaron sprints iniciales de solo 2 días con 56 puntos (28 pts/día) y fue necesario extender el cronograma (CC-01). | El compromiso de sprint debe basarse en la velocidad demostrada del equipo y no en plazos fijos. | Estimar la capacidad real antes de comprometer el backlog del sprint. |
| **3** | Las historias HU-01 a HU-05 de la app se integraron el 27 oct, se revirtieron el 28 y se rehicieron el 29 (18 puntos de retrabajo). | Integrar directamente a `main` sin validación previa de QA genera reprocesos y desestabiliza el código. | Establecer como regla obligatoria que QA revise y apruebe en la rama antes de dar Merge. |
| **4** | La numeración de historias de gestión y desarrollo generaba cruces de identificadores (resuelto en PR #4). | Una taxonomía clara y única evita confusiones en la trazabilidad documental. | Definir identificadores únicos (`HU-XX` para app y `E-XX` para gestión) en el Sprint Planning. |
| **5** | En el Kanban de documentos, el Lead Time fue de 3 días frente a un Cycle Time menor a 1 día. | El cuello de botella radicaba en los tiempos de espera de revisión, no en la redacción. | Respetar estrictamente los límites de WIP por columna y priorizar revisiones pendientes. |
| **6** | Los algoritmos se validaron contra cálculos independientes (hoja *Verificacion*) y 33 pruebas automatizadas (`npm test`). | La verificación cruzada independiente otorga confianza matemática y previene errores en demostración. | Mantener siempre una hoja de contraste independiente en todo desarrollo analítico. |

---

## 3. Plan de Sostenimiento (CA3)

La solución fue diseñada con arquitectura *serverless* y procesamiento local en el navegador del cliente (SheetJS + Chart.js), sin base de datos en nube ni costos recurrentes de licenciamiento (publicable en GitHub Pages y Google Apps Script gratuito):

| Actividad de Sostenimiento | Responsable | Frecuencia | Procedimiento Operativo |
|---|---|:---:|---|
| **Registro de datos de turno** | Administrador y operarios | Por turno | Diligenciar tandas en `Fact_Produccion`, paros en `Fact_Paros` y mano de obra en `Fact_ManoObra`. |
| **Generación del tablero de control** | Administrador de panadería | Mensual | Cargar el libro `.xlsx` en la sección *Cargar datos*, revisar semáforos, alertas y exportar reporte CSV. |
| **Toma de decisiones operativas** | Gerente / Dueño y Administrador | Mensual | Ajustar planes de horneado y pedidos según el % no vendido y cumplimiento de SLA. |
| **Mantenimiento y soporte técnico** | Equipo desarrollador | 2 h / mes | Atender ajustes desde el repositorio, ejecutar `npm test` y regenerar `Backend/Index.html`. |
| **Calibración de metas y parámetros** | Gerente de panadería | Trimestral | Ajustar límites de semáforo en el panel de Metas y actualizar costos de materia prima. |
| **Respaldo de información histórica** | Administrador | Mensual | Guardar copia de seguridad en carpeta local de cada archivo mensual `.xlsx`. |

---

## 4. Acta de Cierre y Transferencia a Operación (CA4)

| Campo | Detalle del Proyecto |
|---|---|
| **Proyecto** | Tablero de Control de Indicadores de Producción de Pan Trenza — Panadería San Nicolás |
| **Fecha de Cierre** | 31 de octubre de 2026 |
| **Objetivo del Proyecto** | Desarrollar una aplicación web interactiva que calcule y visualice el OEE del horno, SLA de pedidos, % no vendido y productividad laboral a partir de un libro de Excel. |
| **Resultado de Entrega** | Aplicación web 100% funcional desplegada en GitHub Pages y Google Apps Script, respaldada por **33 pruebas automáticas aprobadas**, 16 historias de usuario completadas y 109 commits en el repositorio. |
| **Criterio de Éxito 1 (Archivo Distinto)** | Cumplido. Verificado satisfactoriamente con el archivo de octubre de 2026 (42 turnos) y base relacional del curso (4 equipos) sin errores. |
| **Criterio de Éxito 2 (Verificación Matemática)** | Cumplido. Coincidencia exacta con la hoja *Verificacion* en todos los indicadores ($< 10^{-15}$). |
| **Criterio de Éxito 3 (Utilidad para la Decisión)** | Cumplido. Prototipo validado para análisis de cuello de botella, mermas y causas raíz de paros. |
| **Criterio de Éxito 4 (Plazo y Cronograma)** | Cumplido bajo control de cambios CC-01 (ajuste de Sprints 1 y 2 al 31 de octubre). |
| **Entregables Transferidos a la Panadería** | 1. Aplicación Web (GitHub Pages y Google Apps Script).<br>2. Plantilla estandarizada de Excel (`Base_Panaderia_Indicadores.xlsx`).<br>3. Manual de Usuario ([Docs/Manual_Usuario.md](Manual_Usuario.md)).<br>4. Fichas técnicas de los indicadores.<br>5. Repositorio completo con código fuente y suites de prueba. |
| **Capacitación al Administrador** | Realizada mediante manual de usuario interactivo y guía paso a paso de carga. |
| **Firmas de Aceptación y Cierre** | **Patrocinador:** Juan Pablo Velásquez &nbsp;&nbsp;&nbsp;&nbsp; **Product Owner:** Juan José Galicia &nbsp;&nbsp;&nbsp;&nbsp; **QA Lead:** María Camila Tamayo |

---

## 5. Dictamen QA

**✅ APROBADO** — 31 de octubre de 2026

> Se certifica el cumplimiento pleno de la HU-25. Se presenta el cálculo formal del beneficio frente a la línea base con payback de 13 meses, 6 lecciones aprendidas exhaustivas, plan de sostenimiento con roles y periodicidad definidos, y el acta de transferencia y cierre del proyecto debidamente diligenciada.

**Revisado por:** María Camila Tamayo Cuesta — QA Engineer
