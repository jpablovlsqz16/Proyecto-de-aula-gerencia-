# Tablero de Indicadores – Panadería San Nicolás

Aplicación web en **Google Apps Script** que genera un tablero de control con los indicadores de productividad del proceso de producción de **pan trenza** de la Panadería San Nicolás.

Proyecto de Aula 2026-2 · Gerencia de Proyectos · Ingeniería Industrial

## Proceso

Producción de pan trenza: pesaje → amasado → fermentación → división → trenzado → barnizado → fermentación final → **horneado** → enfriado → empaque.
Operación de 2 turnos de 8 horas (06:00–14:00 y 14:00–22:00), 22 días al mes.

## Indicadores

| Indicador | Fórmula |
|---|---|
| OEE del horno | Disponibilidad × Rendimiento × Calidad |
| SLA | Pedidos a tiempo y completos ÷ Total de pedidos |
| % no vendido | (Unidades buenas − Vendidas) ÷ Unidades buenas |
| Productividad | Unidades buenas ÷ Horas-hombre |

## Arquitectura

```
Usuario → HTML/CSS/JS → Google Apps Script → Google Sheets → Dashboard
```

- **Frontend:** HTML, CSS y JS.
- **Backend:** Google Apps Script.
- **Base de datos:** Google Sheets.
- **Despliegue:** Web App de Apps Script, sin servidor externo y sin costo de licencias.

## Uso

1. Abrir el enlace de la aplicación.
2. Cargar el archivo de datos con la estructura de la plantilla `Base_Panaderia_Indicadores.xlsx`.
3. Consultar el tablero y filtrar por fecha, turno o producto.

## Equipo

Metodología: **Scrum**.

| Integrante | Rol |
|---|---|
| Ronal Alexander Álvarez Valencia (docente) | Product Owner |
| Juan Pablo | Scrum Master |
| María Camila | QA |
| Juan José | Desarrollador |
| Iván Santiago | Desarrollador |

## Notas

- Los datos son **simulados con autorización del docente**.
- Se usaron asistentes de IA (Claude); el detalle está en el anexo de declaración de uso de IA del informe.
