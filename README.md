# Movilidad-urbana-y-productividad-economica-en-ciudades-de-LATAM

Proyecto de análisis de datos que evalúa cómo la movilidad urbana (congestión vehicular, tiempos de viaje) se relaciona con la productividad económica (PIB per cápita, desempleo) en las principales ciudades de América Latina, con el fin de identificar en qué ciudades conviene priorizar inversión en infraestructura de transporte.

## Contenido del repositorio
S5_ladb_mobility_economy_project_student.ipynb: notebook con el análisis completo, de carga de datos a conclusiones.
ladb_mobility_economy_2024_clean.csv: dataset final, limpio e integrado, generado como resultado del análisis.


## Fuentes de datos
TomTom Traffic Index (tomtom_traffic.csv): métricas de congestión y tiempos de viaje por ciudad, con registros históricos.
OECD Cities (oecd_city_economy.csv): indicadores económicos por ciudad y año, como PIB per cápita, tasa de desempleo, población y calidad del aire (PM2.5).


## Proceso de análisis
El notebook está organizado en 7 pasos:
1. Carga y exploración: importación de librerías (pandas, numpy, seaborn, matplotlib) y revisión inicial de ambos datasets.
2. Limpieza y preparación: estandarización de nombres de columnas a snake_case, corrección de tipos de datos (fechas y valores numéricos con separadores de miles, comas decimales y símbolos como %).
3. Extracción de año y filtrado: derivación del año a partir de las fechas y filtrado de los registros correspondientes a 2024.
4. Resumen de movilidad: cálculo de promedios anuales de las métricas de tráfico por ciudad, dado que el dataset original tiene múltiples registros por ciudad.
5. Integración de datasets: unión (inner join) de los datos de movilidad y economía usando city y year como claves, conservando solo las ciudades y años presentes en ambas fuentes.
6. Visualización: boxplot de la distribución de jams_delay, histograma del PIB per cápita por ciudad, y gráfico de barras comparando ambas variables por ciudad.
7. Exportación y documentación: guardado del dataset final en CSV y redacción de un resumen ejecutivo con hallazgos y recomendaciones.


## Cobertura de los datos
Año analizado: 2024
Ciudades: 15
Países: 7


## Principales hallazgos
La relación entre movilidad urbana y productividad económica es débil y no lineal cuando se mide mediante la congestión directa (jams_delay); el desempleo resultó ser mejor predictor del PIB per cápita, lo que sugiere que el efecto de la movilidad sobre la productividad pasa más por el mercado laboral (acceso a empleo, costos de desplazamiento, agotamiento del trabajador) que por el tráfico en sí.
Las ciudades más congestionadas (Ciudad de México, Bogotá) no son ni las más pobres ni las más ricas, sino las más grandes y activas en términos de población.
Ciudad de México presenta un valor atípico (outlier) en jams_delay (2833 minutos), muy por encima del límite superior calculado (1942) y de la media general (629.52).
Algunas ciudades con mejor planificación urbana muestran menores tiempos de viaje a pesar de tener un PIB medio.


## Recomendaciones
Ampliar el dataset con series temporales de al menos 5 años, ya que con un solo año no es posible determinar tendencias o cambios.
Incorporar variables de calidad del transporte público, ausentes en este dataset pero relevantes para el mecanismo causal entre movilidad y productividad.
Priorizar Bogotá y Lima para estudios de factibilidad de inversión en infraestructura de transporte.


## Herramientas utilizadas
Python 
pandas, numpy
seaborn, matplotlib

## Cómo ejecutar el proyecto
Clonar o descargar este repositorio.
Asegurarse de tener los archivos tomtom_traffic.csv y oecd_city_economy.csv disponibles en la ruta /datasets/ (o ajustar las rutas en el notebook según corresponda).
Instalar las dependencias necesarias:

Abrir y ejecutar S5_ladb_mobility_economy_project_student.ipynb en Jupyter Notebook o JupyterLab.
El archivo ladb_mobility_economy_2024_clean.csv se generará automáticamente al ejecutar la última celda de exportación.
