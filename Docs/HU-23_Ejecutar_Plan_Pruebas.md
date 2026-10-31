# HU-23 · Ejecutar el Plan de Pruebas y Aseguramiento de Calidad (QA)

**Proyecto:** Tablero de Indicadores · Panadería San Nicolás (Pan Trenza)  
**Responsable:** María Camila Tamayo Cuesta · Ingeniera de Calidad (QA)  
**Sprint:** Sprint 2 / Sprint 3 · Segunda Entrega · Proyecto de Aula 2026-2  
**Fecha de Certificación:** 31 de octubre de 2026  

---

## 1. Objetivo y Alcance

Certificar de manera integral la calidad funcional, exactitud matemática, resiliencia y usabilidad del tablero de control de indicadores para la producción de pan trenza. La estrategia de aseguramiento de calidad (QA) abarca tres niveles complementarios:
1. **Pruebas Automatizadas Unitarias y de Integración (`npm test`):** 33 pruebas automatizadas sin dependencias externas, evaluando normalización de encabezados, parsing numérico/fechas, lógica relacional, fórmulas de fichas técnicas y semáforos.
2. **Pruebas Funcionales y de Caja Negra (CP-01 a CP-08 y E1 a E11):** Verificación de interfaz de usuario, filtros dinámicos, persistencia local (`localStorage`), vista de impresión y exportación de datos.
3. **Validación con Archivo Distinto e Independiente:** Procesamiento del mes de octubre de 2026 (semilla 1029, festivo del 12 de octubre, 42 turnos) y base relacional del curso (4 máquinas), contrastando resultados contra hojas de cálculo independientes.

---

## 2. Criterios de Aceptación (DoD)

| # | Criterio de Aceptación | Estado | Evidencia de Verificación |
|---|------------------------|:------:|---------------------------|
| **CA1** | Cada historia tiene al menos un caso de prueba | ✅ **CUMPLE** | Cada historia cuenta con casos de prueba automatizados en `Tests/` (33 pruebas en total) y casos de caja negra (CP-01 a CP-08) registrados en la Hoja 4 de la Matriz Oficial de QA. |
| **CA2** | Se prueba la carga con un archivo distinto al de desarrollo | ✅ **CUMPLE** | Se ejecutó la prueba con `Base_Panaderia_Indicadores_2026-10.xlsx` (octubre 2026) en `Tests/archivo-distinto.test.js` y caso E4, validando 42 turnos y 7 indicadores idénticos a la hoja *Verificacion*. |
| **CA3** | Los errores encontrados quedan registrados y corregidos | ✅ **CUMPLE** | Registro formal de defectos en la Hoja 5 de la Matriz: BUG-01 (HU-19), BUG-02 (HU-22), BUG-03 (HU-06) y BUG-04 (HU-21), todos resueltos, revalidados y cerrados por QA. |
| **CA4** | El plan y la evidencia quedan como anexo del informe | ✅ **CUMPLE** | Plan consolidado en [Docs/Plan_Pruebas.md](Plan_Pruebas.md), matriz de aprobación oficial [Docs/Matriz_QA_Aprobacion_FINAL 1.2.xlsx] y reportes técnicos individuales por historia en `Docs/`. |

---

## 3. Matriz de Cobertura de Pruebas por Historia de Usuario

| Historia | Módulo / Componente | Caso Automatizado (`Tests/`) | Caso Funcional (Hoja 4 / E2E) | Resultado |
|---|---|---|---|:---:|
| **HU-01** | Arquitectura y estructura | `modelo.test.js` (Estructura base) | CP-01 / E1 (Navegación base) | ✅ PASÓ |
| **HU-02** | Plantilla Excel y diccionario | `modelo.test.js` (9 tablas relacionales) | CP-02 / E2 (Descarga plantilla) | ✅ PASÓ |
| **HU-03** | Simulación de datos | `modelo.test.js` (Carga septiembre) | E3 (Datos de ejemplo) | ✅ PASÓ |
| **HU-04** | Carga de archivo Excel | `lectura.test.js` (Encabezados, formatos) | CP-01 (Lectura sin errores) | ✅ PASÓ |
| **HU-05** | Reconocimiento y validación | `modelo.test.js` (Rechazo filas defectuosas) | CP-02 / E6 (Filas no cargadas) | ✅ PASÓ |
| **HU-06** | OEE del horno (v0) | `oee.test.js` (Cálculo A × R × Q y exclusiones) | CP-03 (Cálculo exacto OEE) | ✅ PASÓ |
| **HU-07** | SLA de pedidos (OTIF) | `sla.test.js` (Pedidos a tiempo y completos) | CP-04 (Proporción SLA) | ✅ PASÓ |
| **HU-08** | % de producto no vendido | `no-vendido.test.js` (Ventas vs producidas) | CP-05 (Merma/no vendido) | ✅ PASÓ |
| **HU-09** | Productividad de mano de obra | `productividad.test.js` (Trenzas / h-h) | CP-06 (Horas-hombre y valor) | ✅ PASÓ |
| **HU-10** | Semáforos y ajuste de metas | `semaforo.test.js` (Límites verde/amarillo/rojo) | E7 (Cambio meta y persistencia) | ✅ PASÓ |
| **HU-11** | Filtros de fecha, turno y equipo | `filtros.test.js` (Rangos temporales y turnos) | CP-07 / E8 (Filtro T1/T2 y recálculo) | ✅ PASÓ |
| **HU-12** | Gráficos del tablero | `graficos.test.js` (Pareto, cascada, series) | E3 (Visualización 6 gráficos) | ✅ PASÓ |
| **HU-13** | Hallazgos automáticos | Test headless `test_hu13_v2.html` (8 hallazgos) | E3 (Panel #alertas) | ✅ PASÓ |
| **HU-14** | Exportar CSV e imprimir | Test headless `test_hu14.html` (BOM, comas, print) | E9 (Apertura CSV y `@media print`) | ✅ PASÓ |
| **HU-15** | Verificación archivo distinto | `archivo-distinto.test.js` (Octubre 2026) | CP-08 / E4 (42 turnos, 7 KPIs) | ✅ PASÓ |
| **HU-16** | Prototipo final publicado | Test headless `test_hu16.html` (Apps Script, Pages) | E10 / E11 (Móvil, offline, `/exec`) | ✅ PASÓ |

---

## 4. Registro y Gestión de Defectos (Bug Tracking)

Conforme al criterio **CA3**, se gestionó la bitácora formal de no conformidades en la Hoja 5 de la Matriz Oficial:

| ID Defecto | Historia | Descripción del Hallazgo | Tipo de Error | Severidad | Asignado a | Estado | Fecha Resolución |
|---|---|---|---|:---:|---|:---:|:---:|
| **BUG-01** | HU-19 | El bloque de 'Canales' en el CANVAS inicial no especificaba canales directos a panaderías aliadas. | Contenido | Media | Juan Pablo | **CERRADO** | 2026-10-30 |
| **BUG-02** | HU-22 | Faltaban enlaces directos a los hashes de commit en la tabla de control de cambios. | Trazabilidad | Alta | Juan Pablo | **CERRADO** | 2026-10-30 |
| **BUG-03** | HU-06 | Duda en la unidad de tiempo ideal (min vs h) en la función de velocidad nominal del horno. | Cálculo | Alta | Juan José | **CERRADO** | 2026-10-30 |
| **BUG-04** | HU-21 | Falta detallar el impacto de las tasas de interés en el flujo de caja en opciones de financiación. | Análisis | Baja | María Camila | **CERRADO** | 2026-10-30 |

Todos los defectos fueron subsanados por los responsables, revalidados por QA y cerrados satisfactoriamente antes de emitir la aprobación final.

---

## 5. Resumen de Pruebas con Archivo Distinto (Octubre 2026)

Se verificó el comportamiento del algoritmo frente al archivo `Base_Panaderia_Indicadores_2026-10.xlsx` (semilla 1029, calendario con festivo del 12 de octubre):

```text
Indicador                      Valor Calculado App        Hoja Verificacion Excel      Diferencia
-------------------------------------------------------------------------------------------------
Disponibilidad (A)             93,6629 %                  93,6629 %                    3,33 × 10⁻¹⁶
Rendimiento (R)                78,8083 %                  78,8083 %                    1,11 × 10⁻¹⁶
Calidad (Q)                    96,2902 %                  96,2902 %                    0,00
OEE Global                     71,0758 %                  71,0758 %                    2,22 × 10⁻¹⁶
SLA de Pedidos (OTIF)          87,6923 %                  87,6923 %                    0,00
% Producto No Vendido           3,6629 %                   3,6629 %                    6,94 × 10⁻¹⁸
Productividad Mano de Obra      8,4237 tn/h-h              8,4237 tn/h-h               0,00
Turnos Procesados: 42 turnos (21 días hábiles × 2 turnos). Errores de validación: 0.
```

---

## 6. Dictamen Final de QA

**✅ APROBADO** — 31 de octubre de 2026

> Como Ingeniera de Calidad (QA), certifico que el software cumple con la totalidad de los criterios de aceptación (DoD), mantiene cero defectos abiertos, pasa el 100% de la suite automatizada (33/33) y demuestra exactitud matemática absoluta ante múltiples conjuntos de datos independientes. El sistema se encuentra listo para entrega y sustentación final.

**Certificado por:** María Camila Tamayo Cuesta — QA Engineer
