# REPORTE FINAL — Segundo corte, electiva de Big Data

**Estudiante:** jsuarez (jsuarez@epsianaswayuu.com)
**Fecha:** 2026-09-22

## 1. Resumen ejecutivo

Se construyó un pipeline completo en Python (pandas, numpy, faker, matplotlib) sobre un dataset sintético de **CRM de clientes**, cubriendo generación, limpieza, ordenamiento/agrupamiento y visualización de datos. Todo el proceso es reproducible (semilla fija `SEED=42`) y quedó documentado paso a paso en [DECISIONS.md](DECISIONS.md), [TASKS.md](TASKS.md) y [MEMORY.md](MEMORY.md).

## 2. Dataset

- **Origen:** generado sintéticamente con `Faker` + `numpy` (no descargado) — ver [DECISIONS.md](DECISIONS.md) #1 y #7.
- **Caso de negocio:** clientes de una empresa (CRM).
- **Script:** [scripts/generar_dataset.py](scripts/generar_dataset.py) → [data/raw/dataset.csv](data/raw/dataset.csv).
- **Volumen crudo:** 8240 filas × 14 columnas (`id_cliente, nombre, email, telefono, fecha_registro, edad, genero, ciudad, plan_contratado, ingresos_estimados, estado, metodo_contacto_preferido, ultima_interaccion, puntaje_satisfaccion`).
- **Suciedad inyectada a propósito:** 5340 valores nulos, 240 filas duplicadas exactas, fechas en 4 formatos distintos, teléfonos en formatos variados, texto con mayúsculas/espacios inconsistentes, outliers en `edad` e `ingresos_estimados`.

## 3. Limpieza

- **Script:** [scripts/limpiar_dataset.py](scripts/limpiar_dataset.py) → [data/processed/dataset_clean.csv](data/processed/dataset_clean.csv).
- **Reglas aplicadas** (detalle y justificación en [DECISIONS.md](DECISIONS.md) #8):
  - Duplicados exactos eliminados (240 filas).
  - Fechas parseadas a `datetime` pese a los 4 formatos de origen (con regla documentada para el caso ambiguo día/mes).
  - `edad` acotada a `[18, 100]` e `ingresos_estimados` a `[1, 20M]`; fuera de rango se imputa con la mediana.
  - `email`/`telefono` nulos → `"no_disponible"`; `telefono` normalizado a solo dígitos/`+`.
  - `ciudad` nula → moda; `nombre`/`ciudad` con capitalización consistente (`strip()` + `title()`).
  - `puntaje_satisfaccion` nulo → mediana.
- **Resultado:** 8000 filas × 14 columnas, **0 nulos, 0 duplicados**.

## 4. Ordenamiento y agrupamientos

- **Script:** [scripts/ordenar_dataset.py](scripts/ordenar_dataset.py).
- `dataset_ordenado.csv`: dataset completo ordenado por `ingresos_estimados` (desc), desempate por `fecha_registro` (asc).
- `ranking_top_clientes.csv`: top 10 clientes por ingresos (máximo ≈ $16.48M).
- `resumen_por_ciudad.csv` / `resumen_por_plan.csv`: conteo y promedios (ingreso/edad/satisfacción) por grupo.
  - Nota: `Santa Marta` concentra más clientes (1433) que el resto (~900-965) porque fue la ciudad usada para imputar los `ciudad` nulos en la limpieza — efecto esperado, no un error.

## 5. Visualización

- **Script:** [scripts/graficar_dataset.py](scripts/graficar_dataset.py) → 4 gráficas en [output/graficas/](output/graficas/), con el estilo definido en [DESIGN.md](DESIGN.md) (paleta azul `#4C72B0`, fondo `#F5F5F5`, un tipo de gráfico por pregunta).

| Pregunta | Gráfica | Hallazgo |
|---|---|---|
| ¿Cómo se distribuyen los ingresos estimados? | Histograma (`01_histograma_ingresos.png`) | Distribución asimétrica a la derecha; la mayoría de clientes gana entre 1M y 3M. |
| ¿Cuántos clientes hay por plan contratado? | Barras (`02_barras_clientes_por_plan.png`) | Los 4 planes están casi parejos (~2000 clientes cada uno), sin un plan dominante. |
| ¿Cómo ha evolucionado el registro de clientes por año? | Línea (`03_tendencia_registros_por_anio.png`) | Volumen estable entre 2022-2025 (~1600/año); 2021 y 2026 salen bajos por ser años parciales dentro de la ventana de generación de 5 años. |
| ¿Hay relación entre edad e ingresos? | Dispersión (`04_dispersion_edad_ingresos.png`) | No se observa correlación clara; los ingresos más altos se concentran entre 30 y 50 años. |

## 6. Conclusiones

- El pipeline cumple los criterios de éxito del [PRD.md](PRD.md): volumen suficiente (miles de filas, 14 columnas), limpieza reproducible y documentada, y 4 visualizaciones que responden preguntas concretas.
- Las decisiones de limpieza (rangos válidos, imputación por mediana/moda) están documentadas y son ajustables si se requiere un criterio distinto.
- Limitación conocida: la ambigüedad de fechas en formato `DD-MM-YYYY` vs. `MM-DD-YYYY` (cuando ambos componentes son ≤ 12) no se puede resolver con certeza absoluta; se optó por una convención documentada.

## 7. Cómo reproducir el pipeline completo

```powershell
venv\Scripts\python.exe scripts\generar_dataset.py
venv\Scripts\python.exe scripts\limpiar_dataset.py
venv\Scripts\python.exe scripts\ordenar_dataset.py
venv\Scripts\python.exe scripts\graficar_dataset.py
```
