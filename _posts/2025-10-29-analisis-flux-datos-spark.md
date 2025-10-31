---
layout: post
title: "Análisis de Flujo de Datos Simulado con Spark y Jekyll"
date: 2025-10-29
categories: analitica spark streaming
author: Alejandro Villoria
---
## 🧠 Introducción

Para el desarrollo de esta actividad se analiza un flujo de datos simulado de una tienda online que permite registrar los clics de los usuarios en tiempo real.  
El objetivo es aplicar analítica avanzada con **Apache Spark** para procesar estos datos y detectar patrones de navegación, usando **Python y Jekyll** para documentar el proceso.

## Objetivo

Aplicar analítica avanzada para procesar un flujo de datos simulado en un contexto empresarial usando Python y Spark, mostrando los resultados dentro de un blog construido con Jekyll.

## Desarrollo del Ejercicio

### 1. Escenario seleccionado
Se simuló una tienda online que registra clics de usuarios. El sistema recibe datos con las columnas:
- `Timestamp` (marca de tiempo)
- `User_ID` (identificador del usuario)
- `Clicks` (número de clics en el sitio)

### 2. Carga del Dataset
Usar un archivo CSV llamado `clickstream_data.csv` con 1000 registros simulados.

from pyspark.sql import SparkSession

spark = SparkSession.builder.appName("ClickStreamAnalysis").getOrCreate()
df = spark.read.csv("clickstream_data.csv", header=True, inferSchema=True)
df.show(5)

### 3. Procesamiento con Spark Streaming (simulado)
Se simula un flujo de datos en ventanas de 1 minuto con el fin de contar clics por usuario, esto se logra con el siguiente código:
import time
from pyspark.sql.functions import col

for i in range(0, 10):
    window_df = df.filter(col("Timestamp").between(i*60, (i+1)*60))
    summary = window_df.groupBy("User_ID").sum("Clicks")
    summary.show()
    time.sleep(1)

### 4. Visualización
Permite generar un gráfico de clics por usuario con matplotlib:
import matplotlib.pyplot as plt
import pandas as pd

data = df.groupBy("User_ID").sum("Clicks").toPandas()
plt.bar(data["User_ID"], data["sum(Clicks)"])
plt.xlabel("Usuario")
plt.ylabel("Total de clics")
plt.title("Clics por usuario - Análisis de Flujo")
plt.show()

![Gráfico de clics por usuario](/assets/images/top10_clicks.png)

## Interpretación y Conclusiones

Se evidencia que algunos usuarios concentran la mayoría de los clics, lo que sugiere que podrían ser clientes frecuentes o bots. Con la ayuda de estos patrones, permiten que la tienda pueda cumplir objetivos concretos, entre ellas se mencionan las siguientes:

- Detectar comportamientos anómalos o automatizados.
- Identificar clientes más activos para promociones personalizadas.
- Ajustar la interfaz del sitio según las zonas de mayor interacción.

**Reflexión:** El procesamiento en *streaming* permite analizar eventos en tiempo real, mientras que el procesamiento por *lotes* analiza grandes volúmenes de datos acumulados después de un periodo.

## Arquitectura y Despliegue del Blog

Este blog está desarrollado con **Jekyll** y el tema **Cayman**.  
La estructura del proyecto incluye:

## Cierre y Retroalimentación

Este proyecto incluye herramientas de **Big Data** y visualización en un entorno reproducible.  
El uso de **Spark Streaming** representa una tendencia esencial en la analítica en tiempo real.  
Gran trabajo con Spark; el *streaming* es clave en 2025.