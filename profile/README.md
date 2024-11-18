# Prueba Técnica Taurus Services

El propósito de esta prueba técnica es construir una solución completa que abarque desde la creación de una base de datos hasta la visualización de los resultados mediante un microservicio API y un frontend interactivo. La solución debe realizar un análisis de datos sobre un conjunto de archivos CSV, proporcionando cálculos clave y permitiendo la visualización de los resultados en tablas y gráficos.

## Descripción del Proyecto

Este proyecto está dividido en tres secciones principales:

1. **Base de Datos (MySQL o MariaDB)**
2. **Microservicio API (FastAPI)**
3. **Frontend (React, AG Grid y Plotly.js)**

Cada una de estas secciones tiene un propósito específico, y en conjunto permiten ofrecer un servicio completo que procesa, consulta y presenta los datos de manera eficiente.

### 1. Base de Datos

#### Objetivo
Construir una base de datos relacional (MySQL o MariaDB) a partir de los archivos CSV proporcionados. La estructura de la base de datos debe estar optimizada para consultas eficientes, y se deben crear las tablas necesarias para almacenar los datos provenientes de los archivos CSV.

#### Proceso

- **Análisis de los Archivos CSV**: Antes de crear la base de datos, es importante revisar los archivos CSV para identificar las entidades y las relaciones entre ellas. Cada archivo CSV representará una tabla en la base de datos.
- **Estructuración de la Base de Datos**: Basado en el análisis previo, se deben crear las tablas correspondientes, asegurándose de definir las claves primarias y foráneas adecuadas para mantener la integridad de los datos.

#### Tareas Específicas
- Importar los archivos CSV a las tablas correspondientes.
- Validar que los datos se hayan cargado correctamente y que no haya inconsistencias o datos faltantes.

---

### 2. Microservicio API (FastAPI)

#### Objetivo
Desarrollar un microservicio con **FastAPI** que permita consultar los datos almacenados en la base de datos y realizar transformaciones o cálculos sobre estos datos. La API debe exponer un conjunto de endpoints que faciliten la obtención de las métricas solicitadas.

#### Consultas y Transformaciones de Datos

La API deberá realizar las siguientes métricas sobre los datos:
- **# Quotes**: Total de cotizaciones registradas.
- **# Quote NB**: Número de cotizaciones únicas.
- **Quote Conversion %**: Porcentaje de conversión entre cotizaciones y cotizaciones exitosas.
- **Quote NB Premium**: Total de primas de cotizaciones de tipo NB (New Business).
- **Average NB Premium**: Promedio de las primas de cotizaciones NB.
- **# PIF**: Número de pólizas activas (PIF: Policies in Force).
- **Expired Policies**: Número de pólizas expiradas.
- **Expired Premium**: Total de la prima de pólizas expiradas.
- **Retention %**: Porcentaje de retención de pólizas, calculado como el número de pólizas renovadas sobre el total de pólizas expiradas.

#### Consideraciones
- Realizar un análisis previo para identificar las relaciones entre las tablas y determinar la forma más eficiente de realizar los cálculos.
- La API debe permitir que los resultados de estas métricas sean consultados en función de diferentes criterios de agrupamiento (por ejemplo, por **tenant** (compañía), **agent** (agente), **estado de la póliza**).

---

### 3. Frontend (React, AG Grid y Plotly.js)

#### Objetivo
Crear una interfaz frontend utilizando **React** para visualizar los resultados de las métricas generadas por la API. La interfaz debe mostrar los datos en tablas interactivas y permitir la exploración de los mismos de manera dinámica.

#### Tareas Específicas

- **Visualización con AG Grid**: Utilizar **AG Grid** para mostrar tres tablas con los resultados agrupados de las métricas. Las tablas deben poder ordenar, filtrar y paginar los datos.
- **Visualización con Plotly.js**: Crear al menos una visualización gráfica utilizando **Plotly.js** que permita explorar las relaciones entre las métricas y los diferentes agrupamientos (por ejemplo, un gráfico que muestre la relación entre la retención y el número de pólizas expiradas por estado).

#### Consideraciones

- El frontend debe consumir la API que hemos creado en el backend para obtener los datos.
- Se deben incluir funcionalidades interactivas como la ordenación y filtrado de las tablas.
- El gráfico debe ser relevante para los datos, proporcionando una forma clara de visualizar las relaciones entre las métricas calculadas.

---

## Análisis de Datos Previo

Antes de realizar cualquier implementación, es importante realizar un análisis de los datos proporcionados en los archivos CSV. Este análisis debe centrarse en:

1. **Identificación de las columnas clave**: Asegurarse de que todas las columnas necesarias para los cálculos estén presentes en los CSV y definir claramente qué datos serán utilizados para cada métrica.
2. **Relaciones entre las tablas**: Determinar cómo se relacionan las diferentes entidades, como cotizaciones, pólizas y agentes. Esto será fundamental para estructurar correctamente la base de datos y las consultas en el backend.
3. **Identificación de posibles inconsistencias**: Revisar los datos en busca de valores nulos, duplicados o fuera de rango, que puedan afectar la calidad de los cálculos y las métricas.

---

## Flujo del Proyecto

1. **Base de Datos**: 
   - Crear tablas a partir de los archivos CSV.
   - Realizar la carga de datos.
   - Verificar la consistencia de los datos.

2. **Microservicio API (FastAPI)**:
   - Implementar los endpoints para las métricas.
   - Realizar consultas optimizadas para las métricas y agrupamientos.
   
3. **Frontend**:
   - Desarrollar la interfaz con React.
   - Integrar AG Grid para mostrar las tablas.
   - Usar Plotly.js para las visualizaciones gráficas.

---

## Requisitos Técnicos

- **Backend**: FastAPI, SQLAlchemy, Databases (para conexión asincrónica a la base de datos)
- **Frontend**: React, AG Grid, Plotly.js
- **Base de Datos**: MySQL o MariaDB
- **Otros**: Docker (opcional para contenerizar el proyecto), herramientas de despliegue como Heroku o AWS (opcional).
