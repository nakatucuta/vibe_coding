# RULES — ¿Qué debe y no debe hacer la IA al programar?

## Regla de oro
**No ejecutar nada (instalar librerías, correr scripts, generar archivos de datos) sin que el usuario lo indique explícitamente.** El usuario ha pedido dejar todo documentado primero y él irá señalando qué ejecutar y en qué archivo.

## Debe hacer
- Trabajar siempre dentro del entorno virtual `venv/` ya creado en la raíz del proyecto.
- Usar `pandas` de forma idiomática (evitar loops `for` sobre filas cuando existe una operación vectorizada equivalente).
- Fijar semillas aleatorias (`np.random.seed`, `Faker.seed()`, `random_state=` en pandas) para que cualquier generación o muestreo de datos sea reproducible.
- Mantener el CSV crudo/original intacto; toda limpieza se guarda en un archivo o variable separada (`data/processed/...`), nunca sobreescribiendo `data/raw/...`.
- Nombrar columnas y archivos en `snake_case`, en español o inglés de forma consistente (no mezclar).
- Seguir PEP8 en el código Python.
- Documentar en [DECISIONS.md](DECISIONS.md) cualquier elección técnica relevante (librería, formato, algoritmo) y por qué se tomó.
- Actualizar [TASKS.md](TASKS.md) y [MEMORY.md](MEMORY.md) conforme avance el proyecto.
- Antes de borrar o sobreescribir un archivo con datos o resultados existentes, confirmar con el usuario.

## No debe hacer
- No instalar paquetes, generar CSVs, ni correr scripts de forma proactiva; esperar indicación explícita del usuario.
- No sobre-diseñar: no crear abstracciones, clases o frameworks que el alcance del ejercicio (electiva, segundo corte) no requiere.
- No agregar manejo de errores o validaciones para casos que no pueden ocurrir en este contexto académico (ej. no hace falta autenticación, ni manejo de concurrencia).
- No usar Spark, Hadoop ni herramientas de clúster: el volumen de datos es simulado y manejable con pandas.
- No usar gráficos 3D, decorativos o con paletas arcoíris (ver [DESIGN.md](DESIGN.md)).
- No dejar código o notebooks a medio terminar; cada script/celda debe ejecutarse de principio a fin sin errores antes de darse por bueno.
- No commitear ni compartir datos sensibles reales (si en algún punto se usa un dataset descargado con información personal real, anonimizar antes de trabajar con él).
