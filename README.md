# 🚕 Optimización Operativa y Análisis de Recaudación - NYC Taxis

Este repositorio contiene el desarrollo del pipeline de procesamiento Batch implementado en **Google Cloud Platform (GCP)** para la asignatura de Big Data.

## 📊 Acceso al Sitio Web del Proyecto
👉 **[Haz clic aquí para ver el Dashboard Interactivo y Resultados](https://tu-usuario.github.io/Proyecto_BigData_Taxis/)**

---

## 🛠️ Arquitectura del Pipeline (GSP823)
El flujo de datos se diseñó de manera desacoplada para procesar **1.5 millones de registros**:
1. **Ingesta:** Archivo original CSV alojado en **Cloud Storage**.
2. **Capa RAW:** Tabla externa creada en **BigQuery** con tolerancia a errores.
3. **ETL / Limpieza:** Filtros de calidad y normalización en **Cloud Dataprep**.
4. **Data Warehouse:** Carga final en tabla nativa de BigQuery y respaldo en **Parquet**.
5. **Analítica:** Modelo predictivo en **BigQuery ML** y reportería en **Looker Studio**.

## 📁 Contenido del Repositorio
* `/sql`: Contiene los scripts de creación de tablas y entrenamiento del modelo predictivo.
* `/transformaciones`: Detalle de la receta lógica utilizada en Dataprep para la limpieza de datos.
* `/docs`: Código fuente del sitio web publicado a través de GitHub Pages.
pichula para el mayron
