# TASKS — ¿Qué se construye ahora y qué sigue después?

Estado general: **✅ Proyecto completo — Fases 0 a 6 ejecutadas.**

## Fase 0 — Entorno (✅ Hecho)
- [x] Crear entorno virtual `venv` en la raíz del proyecto.
- [x] Documentar cómo activarlo (PowerShell / CMD).

## Fase 1 — Documentación (✅ Hecho)
- [x] PRD.md
- [x] ARCHITECTURE.md
- [x] DESIGN.md
- [x] RULES.md
- [x] TASKS.md (este archivo)
- [x] DECISIONS.md
- [x] MEMORY.md

## Fase 2 — Dataset (✅ Hecho)
- [x] Decidir origen final del dataset: **sintético (CRM de clientes)** — confirmado por el usuario 2026-09-22 (ver [DECISIONS.md](DECISIONS.md) #7).
- [x] Instalar dependencias en `venv` (`pandas`, `numpy`, `faker`, `matplotlib`).
- [x] Crear script de generación → [scripts/generar_dataset.py](scripts/generar_dataset.py) → guarda en `data/raw/dataset.csv`.
- [x] Verificar volumen: **8240 filas, 14 columnas**, 5340 valores nulos, 240 filas duplicadas, fechas y teléfonos con formatos inconsistentes, outliers en `edad` e `ingresos_estimados` (ver detalle en [MEMORY.md](MEMORY.md)).

## Fase 3 — Limpieza (✅ Hecho)
- [x] Detectar y tratar valores nulos (mediana/moda/`"no_disponible"` según columna — ver [DECISIONS.md](DECISIONS.md) #8).
- [x] Detectar y eliminar duplicados (240 filas exactas eliminadas).
- [x] Normalizar tipos de datos: fechas parseadas a `datetime` pese a 4 formatos de origen distintos.
- [x] Normalizar texto (`nombre`/`ciudad` con `strip()`+`title()`; `telefono` a solo dígitos).
- [x] Detectar y tratar outliers (`edad` fuera de `[18,100]`, `ingresos_estimados` fuera de `[1,20M]` → imputados con mediana).
- [x] Guardado en [data/processed/dataset_clean.csv](data/processed/dataset_clean.csv) vía [scripts/limpiar_dataset.py](scripts/limpiar_dataset.py) — 8000 filas, 0 nulos, 0 duplicados.

## Fase 4 — Ordenamiento (✅ Hecho)
- [x] Ordenar por columna(s) clave: `ingresos_estimados` (desc) + `fecha_registro` (asc, desempate) → [data/processed/dataset_ordenado.csv](data/processed/dataset_ordenado.csv).
- [x] Ranking top 10 clientes por ingresos → [data/processed/ranking_top_clientes.csv](data/processed/ranking_top_clientes.csv).
- [x] Agrupamiento por ciudad y por plan contratado (conteo, ingreso/edad/satisfacción promedio) → [resumen_por_ciudad.csv](data/processed/resumen_por_ciudad.csv), [resumen_por_plan.csv](data/processed/resumen_por_plan.csv).
- Script: [scripts/ordenar_dataset.py](scripts/ordenar_dataset.py).

## Fase 5 — Visualización (✅ Hecho)
- [x] Definidas 4 preguntas concretas (ver [MEMORY.md](MEMORY.md)).
- [x] Generadas 4 gráficas siguiendo el estilo de [DESIGN.md](DESIGN.md) (paleta azul `#4C72B0`, fondo `#F5F5F5`, un tipo de gráfico por pregunta).
- [x] Guardadas en [output/graficas/](output/graficas/) vía [scripts/graficar_dataset.py](scripts/graficar_dataset.py).

## Fase 6 — Reporte final (✅ Hecho)
- [x] Resumir hallazgos y decisiones tomadas → [REPORTE.md](REPORTE.md).
- [x] Revisado que todo lo ejecutado esté reflejado en [MEMORY.md](MEMORY.md).

## Backlog / ideas futuras (fuera del segundo corte)
- Explorar un dashboard interactivo (Streamlit o artifact HTML) si se requiere en un corte posterior.
- Probar con un dataset real descargado, comparando el proceso de limpieza frente al sintético.
