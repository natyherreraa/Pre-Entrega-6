# Pre-Entrega-6
Análisis de temperaturas diarias en Aeroparque y Ezeiza con Python, SQL y DuckDB a partir de archivos CSV de la NOAA.


## Objetivo

Comparar las temperaturas diarias de Aeroparque Jorge Newbery y del Aeropuerto Internacional Ministro Pistarini (Ezeiza) durante el período observado de 2025. El proyecto utiliza Python, SQL y DuckDB para consultar directamente dos archivos CSV de la NOAA y analizar cómo varían las temperaturas entre ambos aeropuertos.

## Fuente de datos

Se utilizaron los registros diarios del conjunto *Global Surface Summary of the Day* (GSOD) de la NOAA. El análisis comprende 472 registros, 236 por aeropuerto, entre enero y agosto de 2025. 

- [CSV de Aeroparque Jorge Newbery](https://noaa-gsod-pds.s3.amazonaws.com/2025/87582099999.csv)
- [CSV de Ezeiza – Ministro Pistarini](https://noaa-gsod-pds.s3.amazonaws.com/2025/87576099999.csv)

## Cómo ejecutar el análisis

1. Abrir el notebook `.ipynb` de este repositorio en Google Colab.
2. El análisis requiere Python, `duckdb` y `pandas`.
3. Seleccionar **Entorno de ejecución → Ejecutar todas**. El notebook lee los CSV desde sus enlaces y muestra los resultados debajo de cada consulta.


## Preparación y calidad de los datos

DuckDB abre una conexión en memoria y registra los archivos como una vista virtual. Se verifica la cantidad de registros por aeropuerto, se buscan fechas duplicadas y se revisan las temperaturas medias, máximas y mínimas.

La limpieza contempla tanto los valores nulos como el código `9999.9`, que la NOAA utiliza para indicar una temperatura faltante. Ese código se convierte a `NULL` antes de pasar las temperaturas de grados Fahrenheit a Celsius.

En los archivos analizados se encontraron **236 registros por aeropuerto**, sin fechas duplicadas dentro de un mismo aeropuerto ni valores faltantes en las tres variables de temperatura.

