# Manual de usuario — Tablero de control Pan Trenza

## 1. Abrir la aplicación

- **En línea:** enlace de GitHub Pages del repositorio (ver README).
- **Sin internet:** descargar el repositorio y abrir `frontend/index.html` con doble clic en Chrome, Edge o Firefox. No requiere instalación: las librerías vienen incluidas en `frontend/vendor/`.

## 2. Generar el tablero desde un archivo (demostración en vivo)

1. Ir a **Cargar datos** (o arrastrar el archivo sobre cualquier parte de la página).
2. Seleccionar el Excel o CSV. La aplicación:
   - elige la hoja con datos de lotes y encuentra la fila de encabezados,
   - reconoce las columnas por su nombre (ver diccionario de datos),
   - valida cada fila y descarta las que incumplen las reglas.
3. Si están las columnas obligatorias (panes producidos y defectuosos o aprobados), el tablero se genera de inmediato.
4. Si falta alguna, la app queda en **Cargar datos**: en *Correspondencia de columnas* se elige qué columna del archivo corresponde a cada campo y se pulsa **Generar tablero con esta correspondencia**.
5. En *Filas no cargadas* se ve el número de fila y el motivo de cada fila rechazada.

Para probar sin archivo: **Usar datos de ejemplo (simulación)** carga la simulación mensual del repositorio (datos simulados, no reales) y **Usar base OEE de ejemplo** carga la base relacional OEE.
**Descargar plantilla CSV** entrega un archivo vacío con los encabezados recomendados.

## 3. Leer el tablero

- **Tarjetas:** producción total, aprobados, defectuosos, % defectos, % aprobación, productividad, % desperdicio y tiempo promedio. El borde superior indica el semáforo frente a la meta (verde cumple, amarillo a menos de 10 % de la meta, rojo no cumple, gris sin meta).
- **Hallazgos:** resumen automático: cumplimiento de metas, periodos que superan la meta, lotes fuera de control, etapa de mayor duración y periodos de mayor y menor productividad.
- **Gráficos:** producción por periodo, % defectos y % desperdicio con línea de meta, productividad, carta de control p y tiempo promedio por etapa (si el archivo trae tiempos por etapa; la etapa más larga se resalta).
- **Filtros:** rango de periodos (Desde/Hasta), lote y responsable.
- **Metas:** botón *Metas* para cambiar los valores del semáforo; se guardan en el navegador.
- **Exportar CSV:** descarga los lotes filtrados con sus indicadores (separador `;`, abre directo en Excel).
- **Imprimir / PDF:** imprime el tablero sin menús; elegir «Guardar como PDF» en el diálogo.

## 4. Tablero OEE (base relacional)

Si el archivo es un libro con hojas de producción, paros, productos, turnos, motivos de paro, máquinas y operadores, la app muestra el tablero OEE: OEE, disponibilidad, rendimiento, calidad, unidades buenas, productividad de mano de obra, SLA y % no vendido (estos dos solo si el libro trae pedidos y ventas), con filtros por fecha, máquina, línea y turno, gráficos (OEE por día, por máquina y por turno, cascada de tiempo, Pareto de paros y productividad por operador) y hallazgos automáticos. En *Cargar datos* se ve qué hoja se reconoció como cada tabla.

## 5. Preguntas frecuentes

- **¿Dónde quedan los datos?** Solo en el navegador del equipo (localStorage). El archivo no se sube a ningún servidor. Para borrarlo: *Quitar datos del archivo*.
- **El tablero muestra N/D en productividad o desperdicio.** El archivo no tiene columna de tiempo o de materia prima/desperdicio; asignarla en la correspondencia de columnas si existe con otro nombre.
- **Las fechas salen como números.** Asignar la columna al campo *Fecha*: los números de serie de Excel se convierten automáticamente.
