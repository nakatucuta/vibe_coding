# DECISIONS — ¿Por qué elegimos esto y no otra cosa?

Registro de decisiones técnicas para no cambiar de opinión sin querer más adelante. Cada entrada: **decisión → alternativas consideradas → por qué se eligió**.

## 1. Dataset: generar sintéticamente en vez de descargar uno real
- **Alternativas:** descargar un dataset público (Kaggle, datos.gov.co, etc.) vs. generarlo con `Faker`/`numpy`.
- **Elegido (por defecto):** generar sintéticamente.
- **Por qué:** control total sobre el volumen de filas/columnas y sobre qué tipo de "suciedad" (nulos, duplicados, formatos inconsistentes) incluir, lo cual es necesario para que el ejercicio de limpieza tenga sentido pedagógico. Además evita problemas de licencia/atribución y no depende de conexión a internet ni de la disponibilidad de un dataset externo.
- **Reversible:** sí — si el usuario prefiere un dataset real descargado, se puede cambiar sin afectar el resto de la arquitectura (el pipeline de limpieza/ordenamiento/graficación funciona igual sobre cualquier CSV con estructura similar).

## 2. pandas en vez de PySpark/Dask/Polars
- **Alternativas:** PySpark (Big Data real), Polars (más rápido que pandas), Dask (paralelización).
- **Elegido:** pandas.
- **Por qué:** el volumen de datos del ejercicio (miles de filas) no requiere procesamiento distribuido; pandas es el estándar más enseñado y documentado, y es suficiente para limpieza/ordenamiento/graficación en el alcance de una electiva.

## 3. matplotlib (+ opcionalmente seaborn) en vez de Plotly/Bokeh
- **Alternativas:** Plotly/Bokeh (gráficos interactivos), matplotlib/seaborn (gráficos estáticos).
- **Elegido:** matplotlib/seaborn.
- **Por qué:** el entregable no requiere interactividad web; gráficos estáticos son más simples de generar, exportar como imagen y anexar a un informe académico.

## 4. CSV como formato de almacenamiento
- **Alternativas:** base de datos (SQLite/Postgres), CSV plano.
- **Elegido:** CSV.
- **Por qué:** requerimiento explícito del usuario; es portable, fácil de inspeccionar manualmente y suficiente para el volumen de datos manejado.

## 5. Entorno virtual (`venv`) en vez de Conda/Poetry
- **Alternativas:** Conda, Poetry, venv estándar de Python.
- **Elegido:** `venv` (módulo estándar de Python).
- **Por qué:** ya fue creado a solicitud del usuario; no añade dependencias externas de gestión de entornos, y es suficiente para un proyecto de una sola persona/electiva.

## 6. Ejecución solo bajo indicación explícita del usuario
- **Decisión:** no instalar librerías, generar datos ni correr scripts hasta que el usuario lo pida.
- **Por qué:** el usuario pidió explícitamente dejar todo documentado primero y controlar él mismo qué se ejecuta y cuándo.

## 7. Caso de negocio del dataset sintético: Clientes de una empresa (CRM)
- **Alternativas:** Ventas/transacciones de tienda, Clientes (CRM), Empleados/nómina.
- **Elegido:** Clientes de una empresa (CRM).
- **Confirmado por el usuario:** 2026-09-22.
- **Columnas previstas:** `id_cliente`, `nombre`, `email`, `telefono`, `fecha_registro`, `edad`, `ciudad`, `plan_contratado`, `ingresos_estimados`, `estado` (y columnas adicionales para llegar a >10, ej. `genero`, `metodo_contacto_preferido`, `ultima_interaccion`, `puntaje_satisfaccion`).
- **Por qué:** caso de negocio simple de entender, con buena mezcla de tipos de datos (texto, fecha, numérico, categórico) para ejercitar limpieza (nulos, duplicados, formatos inconsistentes) y visualización (distribución por ciudad/plan, edad, ingresos, etc.).

## 8. Reglas de limpieza (Fase 3)
- **Duplicados:** `drop_duplicates()` sobre la fila completa (eran duplicados exactos inyectados a propósito).
- **Fechas (`fecha_registro`, `ultima_interaccion`):** se generaron en 4 formatos (`%Y-%m-%d`, `%d/%m/%Y`, `%m-%d-%Y`, `%d-%m-%Y`). Los formatos con `/` o con año al inicio se detectan sin ambigüedad; para el formato con guiones sin separador distintivo (día-mes vs. mes-día) se usa la regla: si un componente es >12 debe ser el día; si ambos son ≤12 se asume `%m-%d-%Y` por convención, ya que no hay forma de distinguirlos con certeza solo a partir del valor. Es una limitación conocida y documentada, no un bug.
- **Nulos y outliers en `edad`:** rango válido `[18, 100]` (clientes deben ser mayores de edad); todo lo que caiga fuera se trata como inválido y se imputa con la mediana.
- **Nulos y outliers en `ingresos_estimados`:** rango válido `[1, 20_000_000]`; fuera de rango (incluye negativos, cero y valores extremos inyectados) se imputa con la mediana.
- **`email`/`telefono` nulos:** se rellenan con el literal `"no_disponible"` (no tiene sentido imputar un contacto inventado).
- **`telefono`:** se normaliza a solo dígitos y `+` (se descartan espacios, guiones y paréntesis) para unificar formato.
- **`ciudad` nula:** se imputa con la moda (ciudad más frecuente); texto de `nombre`/`ciudad` se limpia con `strip()` + `title()`.
- **`puntaje_satisfaccion` nulo:** se imputa con la mediana.
- **Por qué mediana y no promedio:** la mediana es robusta frente a los outliers extremos que quedaron en el resto de la columna antes de imputar.
