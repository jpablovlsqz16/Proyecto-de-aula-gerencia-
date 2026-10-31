# PROYECTO DE AULA 2026-2 · ETAPA FINAL (20 %)
## TABLERO DE CONTROL DE INDICADORES DEL PROCESO PRODUCTIVO DE PAN TRENZA · PANADERÍA SAN NICOLÁS

**Universidad de Medellín**  
Facultad de Ingenierías · Programa de Ingeniería Industrial  
**Asignatura:** Gerencia de Proyectos (Código 6350) · Grupo 161  
**Docente:** Ronal Alexander Álvarez Valencia  
**Fecha de Entrega y Sustentación:** 29 de octubre de 2026 (20:00 – 22:00)  

---

### EQUIPO DE TRABAJO Y ROLES SCRUM

| Integrante | Rol Scrum / Responsabilidad | Correo Institucional |
| :--- | :--- | :--- |
| **Juan Pablo Velásquez** | Scrum Master / Product Owner / Full-Stack Dev | *Estudiante Ing. Industrial* |
| **María Camila Tamayo Cuesta** | QA Engineer / Aseguramiento de Calidad y Pruebas | *Estudiante Ing. Industrial* |
| **Juan Felipe Ruiz** | Development Team / Analista de Procesos y Datos | *Estudiante Ing. Industrial* |

---

### 🌐 ENLACES OBLIGATORIOS DE ENTREGA (REQUISITO FORMAL DE LA GUÍA)

Conforme a los lineamientos estipulados en la página 2 de la Guía del Proyecto de Aula 2026-2 (*"En la primera página deben aparecer los enlaces al repositorio y a la aplicación"*), a continuación se presentan los accesos directos, públicos y plenamente operativos:

| Canal de Acceso | Tipo de Recurso | Enlace de Acceso Directo | Observaciones / Credenciales |
| :--- | :--- | :--- | :--- |
| **1. Repositorio Oficial de Código** | Repositorio GitHub con Git y trazabilidad completa | [https://github.com/jpablovlsqz16/Proyecto-de-aula-gerencia-](https://github.com/jpablovlsqz16/Proyecto-de-aula-gerencia-) | 109+ commits organizados por Sprints y ramas temáticas de historias de usuario (HU-01 a HU-25). |
| **2. Aplicación Web en Producción** | Despliegue en vivo (GitHub Pages) | [https://jpablovlsqz16.github.io/Proyecto-de-aula-gerencia-/](https://jpablovlsqz16.github.io/Proyecto-de-aula-gerencia-/) | Despliegue en vivo en alta disponibilidad. Carga y procesa libros de Excel sin instalación ni servidor. |
| **3. Web App Institucional** | Google Apps Script (Monolito) | [https://script.google.com/d/18r_gFOM09ovDdwcf_LG0ul88MKnE1V7BeXRePZW3K8W8vyJOLJy1Psch/edit](https://script.google.com/d/18r_gFOM09ovDdwcf_LG0ul88MKnE1V7BeXRePZW3K8W8vyJOLJy1Psch/edit) | Script ID: `18r_gFOM09ovDdwcf_LG0ul88MKnE1V7BeXRePZW3K8W8vyJOLJy1Psch`. Servido por `Backend/Code.gs` e `Index.html`. |
| **4. Ejecución Local (Offline)** | Standalone HTML5 / JavaScript | Abrir archivo local: `Frontend/index.html` | 100 % funcional sin internet gracias a las dependencias embebidas en `Frontend/vendor/`. |

---

### RESUMEN EJECUTIVO Y FICHA TÉCNICA DEL PROYECTO

- **Proceso Productivo Seleccionado:** Fabricación artesanal e industrial de pan trenza (10 etapas: pesaje, amasado, fermentación 1, división, trenzado, barnizado, fermentación final, **horneado [cuello de botella]**, enfriado y empaque).
- **Operación Monitoreada:** 2 turnos diarios de 8 horas (Turno 1: 06:00–14:00 | Turno 2: 14:00–22:00), 22 días al mes (44 turnos operativos).
- **Dimensiones del Tablero de Control:**
  1. **Dimensión Equipo:** OEE del horno de piso continuo (Disponibilidad × Rendimiento × Calidad) — Meta: $\ge 65\ \% $.
  2. **Dimensión Cliente:** SLA de cumplimiento de pedidos (OTIF) — Meta: $\ge 95\ \% $.
  3. **Dimensión Desperdicio:** Porcentaje de producto no vendido — Meta: $\le 10\ \% $.
  4. **Dimensión Personas:** Productividad de mano de obra (unidades buenas / H-H) — Meta: $\ge \text{Línea Base} + 5\ \% $.
- **Garantía de Calidad (QA):** 100 % de casos de prueba superados (33 tests automáticos unitarios e integrados, matriz de 8 casos funcionales E2E sin incidencias críticas abiertas).
- **Validación con Archivo Distinto:** Certificada mediante el procesamiento de la base de datos de octubre de 2026 (42 turnos, 11 028 unidades buenas procesadas en vivo).
