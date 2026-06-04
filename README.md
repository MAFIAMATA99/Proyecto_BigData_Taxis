# 🚖 Plataforma de Analítica de Demanda de Taxis NYC
**Evaluación Parcial N° 2 - Procesos básicos con Big Data (GCP)**

## 📋 Contexto y Problema de Negocio
La New York City Taxi and Limousine Commission (TLC) administra un ecosistema de transporte masivo. Actualmente, enfrenta problemas críticos como:
* Distribución ineficiente de la flota de taxis.
* Congestión en zonas de alta demanda.
* Dificultad para detectar anomalías o fraudes en viajes.

**Objetivo del Proyecto:** Diseñar e implementar un pipeline de datos en modalidad Batch utilizando **Google Cloud Platform (GCP)** para procesar históricos de viajes (aprox. 1.5 a 2 millones de registros), permitiendo limpiar la data y habilitarla para su análisis y toma de decisiones.

---

## 🏗️ Arquitectura de la Solución (Ecosistema GCP)
El flujo técnico diseñado e implementado se basa en una arquitectura *Lakehouse* serverless:

1. **Cloud Storage:** Actúa como *Landing Zone* para la ingesta del dataset en bruto.
2. **BigQuery (Capa RAW):** Motor analítico conectado al almacenamiento externo.
3. **Cloud Dataprep:** Herramienta visual de ETL para la limpieza y curación de datos.
4. **BigQuery (Capa Procesada / DW):** Almacenamiento final de la capa analítica.

---

## 🚀 Ejecución del Pipeline (Evidencias del Laboratorio Batch)

A continuación, se documenta el paso a paso de la implementación en la consola de Google Cloud, incluyendo el manejo de errores.

### 1. Ingesta y Almacenamiento (Data Lake)
Se creó un bucket seguro en **Google Cloud Storage** donde se alojó el archivo original de viajes de taxis en Nueva York.
*(Se aplicó tolerancia a fallos mediante validación de checksums).*

![Evidencia Ingesta en Cloud Storage](evidencias/1_ingesta.png)
*(Nota: Sube tu captura y asegúrate de que la ruta coincida)*

### 2. Creación de Tabla Externa (Capa RAW)
Se integraron los datos crudos creando un dataset en **BigQuery** y definiendo una tabla RAW apuntando directamente a Cloud Storage (sin duplicar datos físicamente). 
*(Se configuró el parámetro `max_bad_records` para ignorar filas corruptas y evitar caídas).*

![Evidencia Tabla RAW BigQuery](evidencias/2_tabla_raw.png)

### 3. Preparación y Transformación (ETL)
Se conectó **Dataprep** a la tabla RAW de BigQuery. Se aplicaron "recetas" analíticas aislando anomalías (por ejemplo, `tarifa < 0`) sin detener el flujo de ejecución principal.

![Evidencia Dataprep](evidencias/3_dataprep.png)

### 4. Data Warehouse y Persistencia Final
Los datos curados y transformados por Dataprep se almacenaron nuevamente en una tabla nativa de BigQuery. Posteriormente, para asegurar el respaldo y la persistencia requerida, se exportó el resultado limpio de regreso a Cloud Storage / Local.

![Evidencia Exportación/Persistencia](evidencias/4_exportacion.png)

---

## 📁 Documentos Entregables

* 📄 [Informe Técnico Completo (Word)](docs/Informe_Tecnico_Taxis_NYC_Final.docx)
* 📊 [Presentación Ejecutiva (PPTX)](docs/Presentacion_Taxis_NYC.pptx)

---
**Desarrollado por:** [Maiquel Puma / Daslav Rivera] - Duoc UC
