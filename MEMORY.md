# MEMORY — ¿En qué punto va el proyecto ahora mismo?

_Última actualización: 2026-09-22_

## Estado actual
- ✅ Entorno virtual `venv` creado en la raíz del proyecto (Python 3.14).
- ✅ Documentación base creada: [PRD.md](PRD.md), [ARCHITECTURE.md](ARCHITECTURE.md), [DESIGN.md](DESIGN.md), [RULES.md](RULES.md), [TASKS.md](TASKS.md), [DECISIONS.md](DECISIONS.md), este archivo.
- ✅ Decidido el origen y caso de negocio del dataset: **sintético, CRM de clientes** (ver [DECISIONS.md](DECISIONS.md) #7).
- ✅ Dependencias instaladas en `venv`: `pandas` 3.0.6, `numpy` 2.5.3, `faker` 40.39.0, `matplotlib` 3.11.2.
- ✅ Dataset generado en `data/raw/dataset.csv` con [scripts/generar_dataset.py](scripts/generar_dataset.py) (semilla fija `SEED=42`, reproducible).
  - **8240 filas × 14 columnas**: `id_cliente, nombre, email, telefono, fecha_registro, edad, genero, ciudad, plan_contratado, ingresos_estimados, estado, metodo_contacto_preferido, ultima_interaccion, puntaje_satisfaccion`.
  - Suciedad intencional: 5340 nulos totales, 240 filas duplicadas exactas, fechas en 4 formatos distintos (`%Y-%m-%d`, `%d/%m/%Y`, `%m-%d-%Y`, `%d-%m-%Y`), teléfonos en formatos variados, texto (`nombre`/`ciudad`) con mayúsculas/espacios inconsistentes, outliers inyectados en `edad` (valores negativos y >100) e `ingresos_estimados` (negativos y extremos).
  - Encoding del CSV: UTF-8 (verificado a nivel de bytes; caracteres acentuados pueden verse mal solo por la consola de Windows, no es un problema del archivo).

- ✅ Dataset limpio en `data/processed/dataset_clean.csv` con [scripts/limpiar_dataset.py](scripts/limpiar_dataset.py) (ver reglas en [DECISIONS.md](DECISIONS.md) #8).
  - **8000 filas × 14 columnas**, 0 nulos, 0 duplicados.
  - `edad` entre 18-78, `ingresos_estimados` entre ~216.854 y ~16.476.293, siempre positivos.
  - Fechas unificadas a `datetime` (formato `YYYY-MM-DD`), teléfonos normalizados a solo dígitos/`+`, `nombre`/`ciudad` con capitalización consistente.

- ✅ Ordenamiento y agrupamientos generados con [scripts/ordenar_dataset.py](scripts/ordenar_dataset.py) (lee `dataset_clean.csv`):
  - `dataset_ordenado.csv`: ordenado por `ingresos_estimados` desc (desempate `fecha_registro` asc).
  - `ranking_top_clientes.csv`: top 10 clientes por ingresos (máximo ~16.48M, cliente id 3446 en Santa Marta).
  - `resumen_por_ciudad.csv` / `resumen_por_plan.csv`: conteo y promedios (ingreso/edad/satisfacción) por grupo.
  - Nota: `Santa Marta` aparece con más clientes (1433 vs. ~900-965 en el resto) porque es la ciudad moda usada para imputar los `ciudad` nulos en la Fase 3 — es un efecto esperado de esa decisión de limpieza, no un error.

- ✅ Visualizaciones generadas con [scripts/graficar_dataset.py](scripts/graficar_dataset.py) en [output/graficas/](output/graficas/), respondiendo 4 preguntas:
  1. **¿Cómo se distribuyen los ingresos estimados?** → `01_histograma_ingresos.png` (distribución asimétrica a la derecha, la mayoría entre 1M-3M).
  2. **¿Cuántos clientes hay por plan contratado?** → `02_barras_clientes_por_plan.png` (los 4 planes están casi parejos, ~2000 clientes c/u).
  3. **¿Cómo ha evolucionado el registro de clientes por año?** → `03_tendencia_registros_por_anio.png` (2021 y 2026 salen bajos porque son años parciales dentro de la ventana de generación `-5y` a `hoy`, no un error de datos).
  4. **¿Hay relación entre edad e ingresos?** → `04_dispersion_edad_ingresos.png` (sin correlación clara visible; los ingresos más altos se concentran entre 30-50 años).

- ✅ Reporte final redactado en [REPORTE.md](REPORTE.md): resume dataset, limpieza, ordenamiento y hallazgos de las 4 gráficas.

## Qué falta
Nada pendiente — **proyecto completo (Fases 0-6)**. Posibles próximos pasos quedan en el backlog de [TASKS.md](TASKS.md) (dashboard interactivo, dataset real descargado), fuera del alcance del segundo corte.

## Próxima acción
Ninguna pendiente. Si el usuario pide ajustes (nuevas gráficas, cambiar reglas de limpieza, otro caso de negocio), retomar desde la fase correspondiente.

## Notas de contexto
- Usuario: jsuarez (jsuarez@epsianaswayuu.com).
- Curso: electiva de Big Data, entregable del **segundo corte**.
- Todo el trabajo debe quedar dentro de `venv` y seguir las reglas de [RULES.md](RULES.md).
