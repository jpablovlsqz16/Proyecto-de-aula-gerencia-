# Manual de usuario — Tablero de indicadores · Panadería San Nicolás

## 1. Abrir la aplicación
- **Aplicación en Producción (GitHub Pages):** [https://jpablovlsqz16.github.io/Proyecto-de-aula-gerencia-/](https://jpablovlsqz16.github.io/Proyecto-de-aula-gerencia-/)
- **Proyecto Web App (Google Apps Script):** [https://script.google.com/d/18r_gFOM09ovDdwcf_LG0ul88MKnE1V7BeXRePZW3K8W8vyJOLJy1Psch/edit](https://script.google.com/d/18r_gFOM09ovDdwcf_LG0ul88MKnE1V7BeXRePZW3K8W8vyJOLJy1Psch/edit)
- **Repositorio Oficial de Código (GitHub):** [https://github.com/jpablovlsqz16/Proyecto-de-aula-gerencia-](https://github.com/jpablovlsqz16/Proyecto-de-aula-gerencia-)
- **Sin internet (Local):** Abrir `Frontend/index.html` con doble clic (Chrome, Edge o Firefox). No requiere instalación ni conexión a internet.

## 2. Preparar los datos
1. En **Cargar datos**, clic en **Descargar plantilla de Excel**.
2. Registrar cada turno: tandas en *Fact_Produccion*, paros en *Fact_Paros*, pedidos en *Fact_Pedidos*, ventas del día en *Fact_Ventas* y horas de cada operario en *Fact_ManoObra*. Las tablas *Dim* ya vienen llenas.
3. Para probar sin datos reales: **Descargar datos simulados** (septiembre de 2026) o **Usar datos de ejemplo**.

## 3. Generar el tablero
Arrastrar el libro de Excel a **Cargar datos** (o a cualquier parte de la página). La aplicación reconoce las tablas por sus columnas, valida las filas y abre el tablero. En *Tablas reconocidas* se ve qué hoja se usó para cada tabla y en *Filas no cargadas* cada fila rechazada con su motivo.

## 4. Leer el tablero
- **Tarjetas:** OEE del horno, disponibilidad, rendimiento, calidad, SLA de pedidos, % no vendido, productividad de mano de obra y trenzas buenas. El borde de color es el semáforo de las fichas técnicas.
- **Hallazgos:** frases con lo más importante: OEE frente a la meta, factor más bajo, causas de paro que suman el 80 %, pedidos tarde e incompletos, no vendido, productividad por turno y día con menor OEE.
- **Gráficos:** OEE por día, cascada de tiempo del horno, Pareto de paros no planeados, SLA y % no vendido por día, productividad por día y OEE por turno.
- **Filtros:** Desde, Hasta y Turno (y Equipo si el archivo trae varias máquinas). Con filtro de turno el % no vendido muestra N/D porque las ventas se registran por día.
- **Metas:** cambiar los límites verde y rojo de cada indicador y la línea base de productividad. **Restaurar valores de las fichas** vuelve a los originales.
- **Exportar CSV** e **Imprimir / PDF**.

## 5. Preguntas frecuentes
- **¿Dónde quedan los datos?** Solo en el navegador del computador. El archivo no se sube a ningún servidor. *Quitar datos cargados* los borra.
- **Una tarjeta dice N/D.** Falta la tabla correspondiente (pedidos, ventas o mano de obra) o el filtro no permite calcularla; la tarjeta explica cuál.
- **No reconoce una tabla.** Revise que los encabezados estén en la primera fila y se parezcan a los del diccionario de datos.
