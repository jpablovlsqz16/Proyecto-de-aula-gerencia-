# HU-09 · Medir la productividad de mano de obra
**Construcción de la Aplicación · Panadería San Nicolás**  
*Proyecto de Aula 2026-2 · Gerencia de Proyectos · Ingeniería Industrial · Universidad de Medellín*

---

| Campo | Detalle |
| :--- | :--- |
| **Historia de usuario** | Como administrador de la panadería, quiero visualizar en el tablero la productividad de la mano de obra (trenzas conformes producidas por cada hora-hombre laborada), para controlar la eficiencia laboral en cada turno y período analizado. |
| **Tipo** | De usuario (lo que ve la panadería) |
| **Responsable** | Juan José (Desarrollador) · Revisa: María Camila (QA) |
| **Estimación** | 3 puntos (Fibonacci) · Prioridad Media |
| **Sprint** | Sprint 3 · miércoles 28 de octubre de 2026 |

---

## 📸 Evidencia Visual de Funcionamiento

A continuación se muestra el módulo **Productividad de Mano de Obra** integrado en el tablero tras procesar la simulación de septiembre 2026. La aplicación calcula la razón consolidada (**8,03 trenzas/h-h** con un total de **652,5 horas-hombre**) y permite desglosar el desempeño por turno operativo:

![Tablero Productividad de Mano de Obra](img/hu09_productividad.png)

---

## 1. Criterios de Aceptación (DoD) y Auditoría Exhaustiva QA

| ID | Criterio de Aceptación | Estado QA | Evidencia y Auditoría Técnica |
| :--- | :--- | :---: | :--- |
| **CA1** | Con septiembre: 8,03 trenzas/h-h con 652,5 horas-hombre. | **CUMPLE** | **Verificado numéricamente al 100%**:<br>• Unidades buenas totales: **5.242 trenzas**.<br>• Horas-hombre laboradas (`Fact_ManoObra`): **652,5 h-h**.<br>• **Productividad = 5.242 / 652,5 = 8,0337 trenzas/h-h** (**8,03**).<br>• Desglose por turnos:<br>&nbsp;&nbsp;– Turno 1 (Mañana): 2.988 trenzas / 328,25 h-h = **9,10 trenzas/h-h**.<br>&nbsp;&nbsp;– Turno 2 (Tarde): 2.254 trenzas / 324,25 h-h = **6,95 trenzas/h-h**.<br>Coincide exactamente con el valor registrado en la hoja `Verificacion` (`8,03`). |
| **CA2** | `npm test` pasa (`Tests/productividad.test.js`). | **CUMPLE** | La suite en `Tests/productividad.test.js` ejecuta las pruebas automatizadas validando:<br>1. Cálculo exacto sobre septiembre (8,0337 trenzas/h-h y 652,5 h-h).<br>2. Algoritmo de contingencia cuando el archivo no trae `Fact_ManoObra`: agrupa por operador calculando horas efectivas a partir de la duración de producción (validado con los 4 operadores de la base académica del curso).<br>Ejecución 100% exitosa sin advertencias. |

---

## 2. Componentes Técnicos Auditados

1. **`Frontend/js/indicadores.js`**:
   - Función `productividadMO(m, produccion, manoObra)`: calcula la relación directa entre piezas conformes y horas trabajadas, ofreciendo agregación global, desagregación por turno y por fecha.
   - Fallback robusto para esquemas sin tabla de asistencia/mano de obra, derivando horas operativas desde los registros de producción por operario.
2. **`Frontend/js/app.js`**:
   - Incorporación de la tarjeta KPI `Productividad de mano de obra` en `#kpis` con formato decimal a 2 dígitos y reporte de horas-hombre totales.
3. **`Backend/Index.html`**:
   - Compilación actualizada (97 KB) conteniendo la lógica de mano de obra integrada para Google Apps Script.
