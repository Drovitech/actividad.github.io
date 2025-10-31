---
layout: default
title: "Análisis de Flujo de Datos Simulado con Spark y Jekyll"
date: 2025-10-29
categories: analitica spark streaming
author: Alejandro Villoria
---
## Introducción

Para el desarrollo de esta actividad se analiza un flujo de datos simulado de una tienda online que permite registrar los clics de los usuarios en tiempo real.  
El objetivo es aplicar analítica avanzada con **Apache Spark** para procesar estos datos y detectar patrones de navegación, usando **Python y Jekyll** para documentar el proceso.

NOTA: Se debe descargar el archivo "analysis.ipynb" y abrirlo en Google Colab para su correcta visualización y ver su funcionamiento.

[Descargar analysis.ipynb](https://download1654.mediafire.com/0qdd62x7zkngSLlq7gZmpp442cqW5oXA9zfpRs1rSse_rBLdgB9ngPkRXcZ5yHddNoML0dZMQ6iTvcoDvgCtbPz4nyxP2it1wHwNmb9wSduVhh7-kBImImR9VlFDEXoiBo60v1cs35eFUe0wsXDLr_ggnhA-IsXWF53yV6VkBKtnxg/z6dvelryuqofn4r/analysis.ipynb)

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
[Descargar archivo CSV](https://download1582.mediafire.com/rl59pci31s4g6_oVfWZgEZOIQiiOmyc3BJ8d0PCy8qL5Ca8kQdW5MRW8gX-w_9zs-PNqrHE9qGJYDQPJFolBj2q1ZzYI2UcMwdKhxqtj4hOH5DP8qBZdMgtj2lKYSI2E4HVOs-8LVCRi1ChbA1VAPePPSOn6A6-zlposXXs05keJxA/mb6hbphh9yvql24/clickstream.csv)

### 3. Procesamiento con Spark Streaming (simulado)
Se simula un flujo de datos en ventanas de 1 minuto con el fin de contar clics por usuario.

### 4. Visualización

Permite generar un gráfico de clics por usuario con matplotlib.

[Ver gráfica](https://drive.google.com/file/d/1v5Ua1jlbMa9GnkZPIl34Y675iAJ5k0kg/view?usp=sharing)

## Interpretación y Conclusiones

Se evidencia que algunos usuarios concentran la mayoría de los clics, lo que sugiere que podrían ser clientes frecuentes o bots. Con la ayuda de estos patrones, permiten que la tienda pueda cumplir objetivos concretos, entre ellas se mencionan las siguientes:

- Detectar comportamientos anómalos o automatizados.
- Identificar clientes más activos para promociones personalizadas.
- Ajustar la interfaz del sitio según las zonas de mayor interacción.

**Reflexión:** El procesamiento en *streaming* permite analizar eventos en tiempo real, mientras que el procesamiento por *lotes* analiza grandes volúmenes de datos acumulados después de un periodo.

## Cierre y Retroalimentación

Este proyecto incluye herramientas de **Big Data** y visualización en un entorno reproducible.  
El uso de **Spark Streaming** representa una tendencia esencial en la analítica en tiempo real.  
Gran trabajo con Spark; el *streaming* es clave en 2025.

## Arquitectura y Despliegue del Blog

Este blog está desarrollado con **Jekyll** y el tema **Cayman**.  

