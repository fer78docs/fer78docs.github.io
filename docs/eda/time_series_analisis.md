---
layout: default
title: Time Series Analysis
nav_order: 5
parent: Exploratory Data Analysis
---

# Analisis de Series Temporales

Los datos de series de tiempo incluyen marcas de tiempo y, a menudo, se generan mientras se monitorea el proceso industrial o se rastrea cualquier métrica comercial. Una secuencia ordenada de valores de marca de tiempo a intervalos igualmente espaciados se denomina serie de tiempo . El análisis de dichas series temporales se utiliza en muchas aplicaciones, como pronósticos de ventas, estudios de servicios públicos, análisis presupuestario, pronósticos económicos, estudios de inventario, etc. Existe una gran cantidad de métodos que se pueden utilizar para modelar y pronosticar series de tiempo.

## Comprender el conjunto de datos de series temporales

La pregunta más esencial sería: ¿qué entendemos por datos de series temporales? Por supuesto, hemos oído hablar de ello en varias ocasiones. ¿Quizás podamos definirlo? Seguro que podemos. Básicamente, una serie de tiempo es una colección de observaciones realizadas de forma secuencial en el tiempo. Tenga en cuenta que aquí hay dos frases clave importantes: **una colección de observaciones** y **secuencialmente en el tiempo**. Como es una serie, tiene que ser una colección de observaciones y, como trata con el tiempo, tiene que hacerlo de forma secuencial.

Tomemos un ejemplo de datos de series de tiempo:
![Serie temporal](https://fer78docs.github.io/assets/images/time_series.webp)

La captura de pantalla anterior ilustra la producción de energía solar (medida en gigavatios hora ( GWh )) durante los primeros seis meses de 2016. También muestra el consumo de electricidad tanto a diario como a semana.

## Fundamentos de la TSA
Para comprender el conjunto de datos de series temporales, generemos aleatoriamente un conjunto de datos normalizado:

