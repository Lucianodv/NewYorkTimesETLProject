# API ETL para el New York Times

## Introducción

En este proyecto realizaremos un proceso de ETL de principio a fin. Para extraer, transformar y cargar datos (ETL) de la API del New York Times (NYT). La API se puede utilizar para recuperar varios tipos de datos del NYT, como artículos, blogs y contenido multimedia. Luego, los datos se pueden transformar a un formato que sea adecuado para cargarlos en un almacén de datos o lago de datos.

Este ejemplo realiza dos llamadas a la API del NYT: una a las noticias más populares y otra a las noticias mensualmente. Las bibliotecas utilizadas son las siguientes:

import os

import configparser

from sqlalchemy import create\_engine

from sqlalchemy import MetaData

from datetime import datetime, timedelta, date

import requests

import pandas as pd

import sqlalchemy as sa

## Extracción de datos

En la primera etapa, se realiza la extracción de datos de la API del NYT. Se recuperan los datos de las noticias más populares y las noticias mensuales. Los datos se guardan en un DataFrame de Pandas.

## Almacenamiento de datos

En la segunda etapa, se almacenan los datos en parquet. Los datos de las noticias más populares se almacenan particionados por categoría de artículo. Las noticias por mes realizamos una particion muy interesante ya que la vamos a particionar por mes y año si esto lo aumatizamos ya sea con airflow u otro sistema al generarse todos los meses podriamos tener una base muy grande almacenada en parquet. 

## Carga de datos

En la última etapa, se cargan los datos en una base de datos PostgreSQL. Se crean las tablas necesarias si no existen. Luego, se cargan los datos de cada dataframe en las tablas correspondientes. 

