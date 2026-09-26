# ARCHITECTURE — ¿Cómo va a funcionar por dentro?

## Stack tecnológico
- **Lenguaje:** Python 3.14
- **Entorno:** entorno virtual (`venv/`) ya creado en la raíz del proyecto.
- **Librerías previstas** (pendientes de instalación, a la espera de indicación del usuario):
  - `pandas` — manipulación, limpieza y ordenamiento de datos.
  - `numpy` — soporte numérico.
  - `faker` — generación de datos sintéticos realistas (nombres, emails, fechas, direcciones) si el dataset se crea en lugar de descargarse.
  - `matplotlib` y/o `seaborn` — visualización de datos (gráficos estáticos).
  - (Opcional) `jupyter` — si se decide trabajar en notebooks en vez de scripts `.py`.

## Estructura de carpetas propuesta
```
segundo corte/
├── venv/                     # entorno virtual (ya creado)
├── data/
│   ├── raw/                  # CSV original, sin tocar (fuente de verdad)
│   └── processed/            # CSV(s) resultantes de la limpieza/ordenamiento
├── scripts/                  # scripts .py (generación, limpieza, graficación)
├── output/
│   └── graficas/             # imágenes de las visualizaciones generadas
├── PRD.md
├── ARCHITECTURE.md
├── DESIGN.md
├── RULES.md
├── TASKS.md
├── DECISIONS.md
└── MEMORY.md
```
> Nota: estas carpetas se crearán solo cuando el usuario indique ejecutar los scripts correspondientes.

## Flujo de datos (pipeline)
1. **Generación/ingesta:** se crea (o descarga) el CSV crudo → `data/raw/dataset.csv`.
2. **Limpieza:** script/notebook que lee el CSV crudo, aplica reglas de limpieza (nulos, duplicados, tipos, formatos) y guarda el resultado en `data/processed/dataset_clean.csv`.
3. **Ordenamiento:** sobre el CSV limpio, se generan vistas ordenadas por columnas relevantes (puede ser el mismo script de limpieza o uno independiente).
4. **Visualización:** a partir del CSV limpio/ordenado se generan gráficas (guardadas en `output/graficas/`) que respondan preguntas concretas del análisis.
5. **Reporte:** opcionalmente, un notebook o markdown final que resuma hallazgos.

## Reproducibilidad
- Todo el código se ejecuta dentro de `venv` para aislar dependencias.
- Los scripts de generación de datos sintéticos usan una semilla fija (`random_state` / `Faker.seed()`) para que el dataset sea reproducible entre ejecuciones.
- El CSV crudo (`data/raw/`) nunca se sobreescribe por los scripts de limpieza; solo se lee.
