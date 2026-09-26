# DESIGN — ¿Cómo se debe ver?

Este proyecto no tiene interfaz de usuario (UI); el "diseño" aplica al **estilo visual de las gráficas y reportes** que se produzcan durante la limpieza, ordenamiento y visualización de datos.

## Paleta de colores
- Usar una paleta consistente y accesible (evitar rojo/verde puro para no afectar a personas con daltonismo).
- Sugerencia de paleta categórica (para comparar categorías):
  - Azul principal: `#4C72B0`
  - Naranja: `#DD8452`
  - Verde: `#55A868`
  - Rojo (usar solo para alertas/outliers): `#C44E52`
  - Gris neutro (fondos, líneas de referencia): `#8C8C8C`
- Para variables continuas/secuenciales (ej. intensidad, cantidad): escala secuencial de un solo tono (ej. azules claro→oscuro), no arcoíris.
- Fondo blanco o gris muy claro (`#F5F5F5`); evitar fondos oscuros por defecto salvo que se pida modo oscuro explícitamente.

## Tipografía
- Fuente sans-serif estándar (ej. `DejaVu Sans` o `Arial`), tamaño de título ≥ 14pt, ejes ≥ 10pt.
- Títulos de gráficos en negrita, subtítulos (si existen) en peso regular.
- Nunca usar fuente decorativa en ejes o etiquetas de datos.

## Estilo de gráficos
- **Un tipo de gráfico por pregunta:** líneas para tendencias en el tiempo, barras para comparar categorías, histogramas/boxplots para distribución, scatter para correlación.
- Cada gráfico debe llevar: título descriptivo (qué pregunta responde), etiquetas de ejes con unidades, leyenda solo si hay más de una serie.
- Evitar gráficos 3D, efectos de sombra o decoraciones que no aporten información (principio de "data-ink ratio" alto).
- Mantener el mismo estilo (misma paleta, misma tipografía) en todas las gráficas del proyecto para dar sensación de reporte unificado.

## Estilo de "botones"/elementos de interacción
- No aplica en esta fase (no hay dashboard interactivo ni app web). Si más adelante se decide construir un dashboard (ej. con Streamlit o un artifact HTML), este archivo se actualizará con guías de botones, espaciado y estados (hover/click).
