# Análisis de Flujo de Datos Simulado con Apache Spark y Jekyll

## Descripción del Proyecto

Este proyecto combina **Big Data** y **desarrollo web estático** mediante **Apache Spark**, **Python** y **Jekyll**.  
Su propósito es analizar un flujo de clics simulados en una tienda online y documentar el proceso de forma visual e interactiva a través de un blog académico.

## Estructura del Proyecto

MI_BLOG/
├── _posts/
│ └── 2025-10-29-analisis-flux-datos-spark.md
├── _config.yml
└── index.md

## NOTA

Los archivos "analysis.ipynb", "clicksteam.csv" se subieron a Mediafire y la gráfica "top 10 usuarios por clics" está en el Drive.

## ⚙️ Análisis con PySpark

El análisis de clics se desarrolló en **Python** utilizando la librería `pyspark` para procesar un dataset con registros simulados de navegación de usuarios.

### **1. Carga del Dataset**

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName("ClickStreamAnalysis").getOrCreate()
df = spark.read.csv("clickstream_data.csv", header=True, inferSchema=True)
df.show(5)

### **2. Procesamiento en Ventanas (Streaming simulado)**
```python
import time
from pyspark.sql.functions import col

for i in range(0, 10):
    window_df = df.filter(col("Timestamp").between(i*60, (i+1)*60))
    summary = window_df.groupBy("User_ID").sum("Clicks")
    summary.show()
    time.sleep(1)

### **3. Visualización de Clics por Usuario**

```python
import matplotlib.pyplot as plt
import pandas as pd

data = df.groupBy("User_ID").sum("Clicks").toPandas()

plt.figure(figsize=(8,4))
plt.bar(data["User_ID"], data["sum(Clicks)"], color="#1f77b4")
plt.xlabel("Usuario")
plt.ylabel("Total de clics")
plt.title("Clics por Usuario - Análisis de Flujo")
plt.tight_layout()
plt.savefig("assets/images/top10_clicks.png")
plt.show()

## Arquitectura y Despliegue del Blog

La arquitectura del blog está basado en una integración entre el procesamiento de datos con Apache Spark y la publicación web mediante Jekyll, lo cual crea un flujo completo desde la generación hasta la visualización de resultados. Los datos simulados del archivo (clickstream.csv) son analizados con PySpark en un entorno de notebook (analysis.ipynb), donde se procesan y visualizan los clics de los usuarios.
 
Por otra parte, los resultados, gráficos e interpretaciones se exportan como archivos estáticos (top10_clicks.png) para que se integren en el sitio desarrollado con Jekyll y el tema Cayman. Finalmente, el despliegue se realiza en GitHub Pages, permitiendo publicar el blog directamente desde el repositorio y garantizando un entorno accesible y profesional para la divulgación del presente análisis.

## Conclusiones del análisis

El análisis del flujo de clics con Apache Spark muestra patrones de comportamiento en tiempo real dentro de una tienda online simulada, lo que permitiría identificar tanto usuarios altamente activos como posibles interacciones automatizadas. Con la implementación de Python y Spark Streaming, se logró demostrar la eficacia del procesamiento distribuido con la misión de manejar grandes volúmenes de datos y obtener información en segundos. Así mismo, la documentación por medio de Jekyll facilita la presentación visual y estructurada de los resultados. Por lo tanto, se convierte en una solución completa que combina analítica avanzada, visualización y publicación web en un mismo entorno reproducible.

