# TFM_NASA

Estructura del Repositorio
Organización General
Este repositorio contiene todos los scripts y datos necesarios para reproducir los análisis del TFM, organizados según los escenarios experimentales correspondientes.
Estructura de Carpetas
📁 gen/ - Carpeta Principal
Contenido:

Archivos de conteos brutos de ARN (gene raw counts): Datos procesados listos para análisis en R
Metadatos de cada escenario: Archivos que especifican qué datasets utilizar en cada script
Archivos del genoma de referencia:

.fna: Secuencias genómicas de las cepas de S. aureus
.gff: Anotaciones genómicas correspondientes



Uso: Esta carpeta contiene todos los archivos necesarios para ejecutar los scripts de análisis y generar los gráficos correspondientes.
📁 pipeline_linux_R/ - Pipeline Completo de Análisis
Estructura organizada por pasos secuenciales:

Scripts en R:

Nomenclatura: *Escenario_a_elegir*_C001_90_condicion.R
Análisis estadístico y visualización de datos


Scripts en Python (.py):

Procesamiento de datos complementario
Análisis bioinformáticos específicos


Archivos intermedios:

Métricas de genes procesadas
Resultados parciales para consultas adicionales
Archivos de verificación y control de calidad



Instrucciones de uso: Ejecutar los scripts siguiendo el orden numérico establecido en las carpetas.
📁 Carpetas de Escenarios Experimentales
Cada carpeta de escenario contiene:

Archivos BAM procesados:

Single-end reads
Paired-end reads


Conteos de ARN derivados de estos archivos BAM
Scripts específicos para cada condición experimental

📁 Carpetas No Utilizadas

riboswitch/ y otras carpetas: Preparadas para análisis futuros pero no empleadas en este estudio por limitaciones de tiempo.

Datos No Incluidos
Archivos Raw de Secuenciación

Origen: Repositorios públicos de la NASA
Tamaño: 20-30 GB por archivo
Motivo de exclusión: Limitaciones de espacio en el repositorio
Procesamiento: Realizado mediante scripts en Bash (preprocesamiento incluido)

Archivos de Preprocesamiento

Scripts en Bash para procesamiento inicial
Pipelines de control de calidad
Archivos de configuración para herramientas bioinformáticas

Requisitos del Sistema
Software Necesario

R (versión recomendada: ≥ 4.0)
Python (versión recomendada: ≥ 3.8)
Bash (para sistemas Linux/Unix)

Dependencias de R
r# Instalar paquetes necesarios
install.packages(c("DESeq2", "ggplot2", "dplyr", "tidyr"))
Dependencias de Python
bashpip install pandas numpy matplotlib seaborn biopython
Instrucciones de Uso
Paso 1: Preparación

Clonar el repositorio
Verificar que todos los archivos de la carpeta gen/ están presentes
Instalar dependencias necesarias

Paso 2: Ejecución del Pipeline

Navegar a la carpeta pipeline_linux_R/
Ejecutar scripts en orden secuencial:
bash# Ejemplo de ejecución
Rscript 01_preprocessing.R
python 02_quality_control.py
Rscript 03_differential_expression.R


Paso 3: Interpretación de Resultados

Los gráficos se generan automáticamente en carpetas output/
Los archivos intermedios permiten verificaciones adicionales
Consultar metadatos para interpretación de condiciones experimentales

Notas Importantes

Reproducibilidad: Todos los scripts están documentados con parámetros específicos
Escalabilidad: El pipeline puede adaptarse para analizar escenarios adicionales
Verificación: Archivos intermedios disponibles para validación de resultados
Documentación: Cada script incluye comentarios detallados sobre su función específica

Contacto y Soporte
Para dudas sobre la implementación o uso de los scripts, consultar la documentación interna de cada archivo o contactar al autor del TFM


Link for the rest of the data: https://drive.google.com/drive/folders/1z_NmSDT8XgkXmA5JoeHt7BkVoGJUVD8r?usp=sharing
están subidos en drive ya que son muy pesados para github
