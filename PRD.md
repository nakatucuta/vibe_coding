# PRD — Product Requirements Document

## ¿Qué construimos y por qué?

### Contexto
Proyecto académico para la electiva de **Big Data**, correspondiente al **segundo corte**. El entregable central es un flujo de trabajo sobre un dataset en formato CSV que demuestre competencia en tres etapas: **limpieza**, **ordenamiento** y **graficación (visualización)** de datos.

### Problema a resolver
Se necesita un conjunto de datos (CSV) con **muchas filas y columnas**, que incluya intencionalmente inconsistencias típicas de datos reales (valores nulos, duplicados, formatos inconsistentes, outliers), para poder aplicar y evidenciar técnicas de limpieza y transformación de datos, y luego generar visualizaciones que comuniquen hallazgos.

### Usuario
- **Estudiante:** jsuarez (jsuarez@epsianaswayuu.com)
- **Rol:** desarrolla y entrega el ejercicio de la electiva.
- **Necesidad:** contar con datos realistas para trabajar, y con un entorno de trabajo (Python + venv) ya preparado, documentado y reproducible.

### Funciones principales (alcance del proyecto)
1. **Obtención/generación de datos:** dataset CSV con alto volumen de filas y columnas (sintético o descargado), representativo de un caso de negocio (p. ej. ventas, transacciones, clientes).
2. **Limpieza de datos:** tratamiento de nulos, duplicados, tipos de datos incorrectos, texto inconsistente (mayúsculas/minúsculas, espacios), fechas mal formateadas, outliers.
3. **Ordenamiento de datos:** ordenar el dataset por una o varias columnas (ascendente/descendente), agrupamientos y rankings.
4. **Visualización de datos:** gráficas que respondan preguntas concretas sobre el dataset (tendencias, distribución, comparación entre categorías).
5. **Documentación del proceso:** justificar decisiones técnicas y dejar registro del avance (ver [DECISIONS.md](DECISIONS.md) y [MEMORY.md](MEMORY.md)).

### Fuera de alcance
- Big Data "real" (no se usará Spark/Hadoop ni clústeres); el volumen de datos es simulado para fines pedagógicos y manejable con pandas.
- Despliegue en producción o exposición como servicio web.
- Bases de datos externas (todo el trabajo parte de un archivo CSV local).

### Criterios de éxito
- El CSV generado tiene un volumen suficiente de filas (miles) y columnas (>10) con datos "sucios" reales de limpiar.
- El proceso de limpieza es reproducible y documentado (qué se limpió y por qué).
- Existen al menos 3-4 visualizaciones distintas que respondan preguntas concretas sobre los datos.
- Todo el código corre dentro del entorno virtual (`venv`) ya creado en el proyecto.
