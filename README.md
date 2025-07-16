# TFM_NASA

# Estructura del Repositorio

## Organización General

Este repositorio contiene todos los scripts y datos necesarios para reproducir los análisis del TFM, organizados según los escenarios experimentales correspondientes.

## Estructura de Carpetas

### 📁 `cargar_archivos_1_escenarios_R/` - Carpeta Principal
**Contenido:**
- **Archivos de conteos brutos de ARN** (*gene raw counts*): Datos procesados listos para análisis en R
- **Metadatos de cada escenario**: Archivos que especifican qué datasets utilizar en cada script
- **Archivos del genoma de referencia**:
  - `.fna`: Secuencias genómicas de las cepas de *S. aureus*
  - `.gff`: Anotaciones genómicas correspondientes

**Uso:** Esta carpeta contiene todos los archivos necesarios para ejecutar los scripts de análisis y generar los gráficos correspondientes.

### 📁 `pipeline_linux_R/` - Pipeline Completo de Análisis
**Estructura organizada por pasos secuenciales:**

1. **Scripts en R**: 
   - Nomenclatura: `*Escenario_a_elegir*_C001_90_condicion.R`
   - Análisis estadístico y visualización de datos

2. **Scripts en Python** (`.py`):
   - Procesamiento de datos complementario
   - Análisis bioinformáticos específicos

3. **Archivos intermedios**:
   - Métricas de genes procesadas
   - Resultados parciales para consultas adicionales
   - Archivos de verificación y control de calidad

**Instrucciones de uso:** Ejecutar los scripts siguiendo el orden numérico establecido en las carpetas.

### 📁 Carpetas de Escenarios Experimentales
Cada carpeta de escenario contiene:
- **Archivos BAM procesados**:
  - Single-end reads
  - Paired-end reads
- **Conteos de ARN derivados** de estos archivos BAM
- **Scripts específicos** para cada condición experimental

### 📁 Carpetas No Utilizadas
- `riboswitch/` y otras carpetas: Preparadas para análisis futuros pero no empleadas en este estudio por limitaciones de tiempo.

## Datos No Incluidos

### Archivos Raw de Secuenciación
- **Origen**: Repositorios públicos de la NASA
- **Tamaño**: 20-30 GB por archivo
- **Motivo de exclusión**: Limitaciones de espacio en el repositorio
- **Procesamiento**: Realizado mediante scripts en Bash (preprocesamiento incluido)

### Archivos de Preprocesamiento
- Scripts en Bash para procesamiento inicial
- Pipelines de control de calidad
- Archivos de configuración para herramientas bioinformáticas

## Requisitos del Sistema

### Software Necesario
- **R** (versión recomendada: ≥ 4.0)
- **Python** (versión 3.10 - especificada en el entorno conda)
- **Bash** (para sistemas Linux/Unix)
- **Conda/Mamba** (para gestión de entornos)

### Configuración del Entorno Conda

El proyecto incluye un archivo `environment.yml` que define el entorno conda con todas las herramientas bioinformáticas necesarias:

```yaml
name: TFM_project_env
channels:
  - conda-forge
  - bioconda
  - defaults
channel_priority: strict
dependencies:
  - python=3.10
  - fastqc=0.11.9
  - trimmomatic=0.39
  - bowtie2=2.5.4
  - htseq=2.0.5
  - kraken2=2.1.3
  - samtools=1.21
```

#### Instalación del Entorno:
```bash
# Crear el entorno desde el archivo YAML
conda env create -f environment.yml

# Activar el entorno
conda activate TFM_project_env

# Verificar instalación
conda list
```

### Herramientas Bioinformáticas Incluidas
- **FastQC** (0.11.9): Control de calidad de secuencias
- **Trimmomatic** (0.39): Limpieza y filtrado de reads
- **Bowtie2** (2.5.4): Alineamiento de secuencias
- **HTSeq** (2.0.5): Conteo de reads en genes
- **Kraken2** (2.1.3): Clasificación taxonómica
- **SAMtools** (1.21): Manipulación de archivos BAM/SAM

### Dependencias de R
```r
# Instalar paquetes necesarios
install.packages(c("DESeq2", "ggplot2", "dplyr", "tidyr"))
```

### Dependencias de Python Adicionales
```bash
# Activar entorno conda primero
conda activate TFM_project_env

# Instalar paquetes adicionales si es necesario
pip install pandas numpy matplotlib seaborn biopython
```

## Instrucciones de Uso

### Paso 1: Preparación del Entorno
1. Clonar el repositorio
2. Crear y activar el entorno conda:
   ```bash
   conda env create -f environment.yml
   conda activate TFM_project_env
   ```
3. Verificar que todos los archivos de la carpeta `cargar_archivos_1_escenarios_R/` están presentes
4. Instalar dependencias adicionales de R si es necesario

### Paso 2: Ejecución del Pipeline
1. Navegar a la carpeta `pipeline_linux_R/`
2. Ejecutar scripts en orden secuencial:
   ```bash
   # Ejemplo de ejecución (con entorno conda activado)
   Rscript 01_preprocessing.R
   python 02_quality_control.py
   Rscript 03_differential_expression.R
   ```

### Paso 3: Interpretación de Resultados
- Los gráficos se generan automáticamente en carpetas `output/`
- Los archivos intermedios permiten verificaciones adicionales
- Consultar metadatos para interpretación de condiciones experimentales

## Notas Importantes

- **Reproducibilidad**: Todos los scripts están documentados con parámetros específicos
- **Escalabilidad**: El pipeline puede adaptarse para analizar escenarios adicionales
- **Verificación**: Archivos intermedios disponibles para validación de resultados
- **Documentación**: Cada script incluye comentarios detallados sobre su función específica

## Contacto y Soporte

Para dudas sobre la implementación o uso de los scripts, consultar la documentación interna de cada archivo o contactar al autor del TFM.


Link for the rest of the data: https://drive.google.com/drive/folders/1z_NmSDT8XgkXmA5JoeHt7BkVoGJUVD8r?usp=sharing
están subidos en drive ya que son muy pesados para github
