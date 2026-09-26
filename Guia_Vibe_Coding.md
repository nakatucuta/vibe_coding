# Vibe Coding: Guía Completa de Principiante a Producción

### De la Idea → Planificación → Programación con IA → Pruebas → Despliegue → Producción

---

## 1. El Flujo de Trabajo Completo de Vibe Coding

Antes de escribir cualquier código, entiende todo el proceso.

IDEA
↓
INVESTIGACIÓN
↓
DEFINIR AL USUARIO
↓
PRD (Documento de Requisitos del Producto)
↓
ELEGIR EL STACK TECNOLÓGICO
↓
ARQUITECTURA
↓
DISEÑO
↓
REGLAS DEL PROYECTO
↓
DESGLOSE DE TAREAS
↓
CONFIGURACIÓN
↓
DESARROLLO
↓
PRUEBAS
↓
REVISIÓN DE SEGURIDAD
↓
REVISIÓN DE CÓDIGO
↓
DESPLIEGUE DE VISTA PREVIA
↓
PRUEBAS DE QA
↓
DESPLIEGUE A PRODUCCIÓN
↓
MONITOREO
↓
ITERACIÓN

Nunca saltes directamente de:

IDEA → IA → DESPLIEGUE

---

## 2. Paso 1: Define qué Quieres Construir

Antes de abrir tu herramienta de IA para programar, responde cinco preguntas.

### 1. ¿Qué problema estás resolviendo?

Ejemplo:

Los estudiantes universitarios tienen dificultades para organizar tareas, notas y fechas límite.

### 2. ¿Quién es el usuario?

Ejemplo:

Estudiantes de BCA, BSc en Ciencias de la Computación y BTech.

### 3. ¿Cuál es el resultado principal?

Ejemplo:

Darle a los estudiantes un solo lugar para gestionar su trabajo académico.

### 4. ¿Cuál es el MVP?

MVP significa Producto Mínimo Viable.

Por ejemplo:

- Autenticación
- Panel de control (Dashboard)
- Notas
- Tareas
- Fechas límite

No empieces con:

- Tutor de IA
- Comunidad
- Pagos
- Aplicación móvil
- Gamificación
- Feed social

Construye primero el producto principal.

### 5. ¿Qué NO forma parte de la primera versión?

Esto es igual de importante.

Ejemplo:

Fuera de alcance:

- Aplicación móvil
- Pagos
- Chatbot de IA
- Funciones sociales

Esto evita que la IA siga expandiendo el proyecto continuamente.

---

## 3. Paso 2: Investiga Antes de Programar

No le pidas a la IA que construya una idea que no has investigado.

Investiga:

### Usuarios

- ¿Quién necesita esto?
- ¿Cuáles son sus problemas?
- ¿Qué alternativas ya existen?

### Competidores

Analiza:

- Funcionalidades
- Interfaz de usuario
- Precios
- Experiencia de usuario
- Fortalezas
- Debilidades

### Viabilidad técnica

Revisa:

- APIs
- Autenticación
- Requisitos de base de datos
- Servicios de terceros
- Hosting
- Costo

### Las herramientas de IA pueden ayudar con la investigación

Puedes usar:

- ChatGPT
- Perplexity
- Google
- Documentación oficial
- GitHub
- Stack Overflow

Para decisiones técnicas, prefiere la documentación oficial antes que artículos de blog aleatorios.

---

## 4. Paso 3: Elige tu Herramienta de IA para Programar

No uses la misma herramienta para todos los proyectos.

### Para principiantes

#### Replit

Bueno cuando quieres:

- Desarrollo basado en el navegador
- Configuración mínima
- Prototipos rápidos
- Experimentación full-stack

#### Lovable

Bueno para:

- Aplicaciones web
- Prototipos de SaaS
- Aplicaciones centradas en la interfaz
- Desarrollo rápido de MVP

#### Bolt

Bueno para:

- Prototipos rápidos de aplicaciones web
- Proyectos JavaScript/TypeScript
- Desarrollo basado en navegador

#### Cursor

Bueno cuando quieres:

- Más control
- Repositorios existentes
- Proyectos más grandes
- Desarrollo local
- Flujos de trabajo profesionales

#### Claude Code

Bueno para:

- Desarrollo basado en terminal
- Bases de código más grandes
- Tareas a nivel de repositorio
- Flujos de trabajo de desarrollo agéntico

---

## 6. Stack Recomendado para Principiantes

Si te tomas en serio aprender desarrollo a través de vibe coding, este es un buen stack inicial:

| Elemento | Herramienta/Tecnología |
|---|---|
| IDE de IA | Cursor |
| Frontend | Next.js |
| Lenguaje | TypeScript |
| Estilos | Tailwind CSS |
| Base de datos | PostgreSQL / Supabase |
| Autenticación | Supabase Auth |
| Control de versiones | Git + GitHub |
| Pruebas | Playwright |
| Despliegue | Vercel |

---

## 7. Paso 4: Instala el Entorno de Desarrollo

Para un proyecto web típico, instala:

### Obligatorio

1. Cursor o VS Code
2. Git
3. Node.js LTS
4. npm
5. Cuenta de GitHub
6. Navegador web moderno

### Opcional

- Docker
- GitHub CLI
- Postman / Bruno
- Cliente de base de datos
- Vercel CLI

Verifica tu instalación:

```
node --version
npm --version
git --version
```

---

## 8. Paso 5: Crea tu Proyecto

Crea una carpeta de proyecto:

```
mkdir student-dashboard
cd student-dashboard
```

Inicializa Git:

```
git init
```

Luego crea un repositorio en GitHub.

Desde el principio, tu proyecto debe tener control de versiones.

¿Por qué?

Porque la IA puede romper tu proyecto.

Git te da la capacidad de:

Cambiar → Probar → Romper algo → Comparar → Revertir

---

## 9. Paso 6: Crea la Documentación de tu Proyecto

Esta es una de las partes más importantes del vibe coding estructurado.

Antes de pedirle a la IA que construya funcionalidades, crea el contexto de tu proyecto.

Un proyecto profesional puede tener:

```
project/
│
├── docs/
│ ├── PRD.md
│ ├── ARCHITECTURE.md
│ ├── DESIGN.md
│ ├── TEST_PLAN.md
│ ├── SECURITY.md
│ ├── DECISIONS.md
│ └── MEMORY.md
│
├── .cursor/
│ └── rules/
│
├── src/
├── tests/
│
├── README.md
├── TASKS.md
├── .env.example
└── .gitignore
```

No necesitas todo esto para un proyecto pequeño.

Para un proyecto de principiante, comienza con:

- PRD.md
- ARCHITECTURE.md
- DESIGN.md
- RULES.md
- TASKS.md
- README.md
- .env.example

---

## 10. Paso 7: Crea PRD.md

### ¿Qué es un PRD?

PRD = Documento de Requisitos del Producto (Product Requirements Document)

Define:

¿Qué estamos construyendo y por qué?

Ejemplo:

```markdown
# Documento de Requisitos del Producto

## Producto
StudentHub

## Problema
Los estudiantes tienen dificultades para gestionar sus
notas académicas, tareas y fechas límite.

## Usuarios objetivo
Estudiantes de BCA, BSc en Ciencias de la Computación y BTech.

## Objetivo
Crear un panel centralizado de productividad académica.

## Funcionalidades principales
1. Autenticación
2. Panel de control
3. Notas
4. Tareas
5. Fechas límite

## MVP
- Registro
- Inicio de sesión
- Panel de control
- Crear notas
- Editar notas
- Eliminar notas
- Crear tareas

## Fuera de alcance
- Pagos
- Tutor de IA
- Aplicación móvil
- Feed social

## Criterios de éxito
Un usuario debería poder:
1. Crear una cuenta
2. Iniciar sesión
3. Crear una nota
4. Editar una nota
5. Eliminar una nota
6. Crear una tarea
7. Marcar una tarea como completada
```

### Recuerda:

PRD = QUÉ + POR QUÉ

---

## 11. Paso 8: Crea ARCHITECTURE.md

Esto define:

¿Cómo funcionará la aplicación?

Ejemplo:

```markdown
# Arquitectura

## Frontend
Next.js + TypeScript

## Estilos
Tailwind CSS

## Backend
Funcionalidad del lado del servidor de Next.js

## Base de datos
Supabase PostgreSQL

## Autenticación
Supabase Auth

## Despliegue
Vercel

## Arquitectura
Usuario → Interfaz Next.js → Server Action / API → Supabase → PostgreSQL
```

Define también tu estructura de carpetas:

```
src/
├── app/
├── components/
├── features/
├── services/
├── lib/
├── types/
└── utils/
```

Define también reglas arquitectónicas.

Ejemplo:

- Los componentes de la interfaz no deben contener lógica de base de datos.
- Las operaciones de base de datos van en los servicios.
- La autenticación debe verificarse del lado del servidor.
- La interfaz reutilizable debe colocarse en componentes.
- La lógica de negocio debe mantenerse separada de la interfaz.

### Recuerda:

Arquitectura = CÓMO

---

## 12. Paso 9: Crea DESIGN.md

Esto le da a la IA un sistema visual consistente.

Sin esto, podrías obtener:

- Página 1 → tarjetas redondeadas
- Página 2 → tarjetas cuadradas
- Página 3 → botones diferentes
- Página 4 → tipografía completamente distinta

Define:

```markdown
# Sistema de Diseño

## Estilo
Moderno, minimalista, profesional

## Tipografía
Inter

## Colores
- Primario: #6366F1
- Fondo: #F8FAFC
- Texto: #0F172A
- Atenuado: #64748B

## Botones
Primario, Secundario, Destructivo

## Tarjetas
Radio de borde: 12px

## Requisitos de UX
- Responsive para móviles
- Estados de carga
- Estados vacíos
- Estados de error
- Formularios accesibles
```

### Recuerda:

DESIGN.md = CÓMO SE VE Y SE SIENTE

---

## 13. Paso 10: Crea RULES.md

Este es el manual de reglas de IA de tu proyecto.

Ejemplo:

```markdown
# Reglas de Desarrollo

## General
- Usa TypeScript.
- Reutiliza componentes existentes.
- No dupliques lógica.
- Mantén las funciones pequeñas.
- No modifiques archivos no relacionados.

## Antes de programar
- Lee la documentación relevante del proyecto.
- Inspecciona la implementación existente.
- Reutiliza la funcionalidad existente cuando sea posible.
- Haz un plan para cambios grandes.

## Interfaz
- Sigue DESIGN.md.
- Mantén el diseño responsive.
- Incluye estados de carga.
- Incluye estados de error.
- Incluye estados vacíos.

## Seguridad
- Nunca expongas claves de API.
- Valida la entrada del usuario.
- Verifica la autorización del lado del servidor.

## Pruebas
- Agrega pruebas para funcionalidad importante.
- Ejecuta las pruebas después de implementar.
- Corrige las pruebas fallidas antes de continuar.

## Git
- Haz commits pequeños.
- Usa mensajes de commit descriptivos.
```

Para Cursor, estas reglas también pueden organizarse dentro de:

```
.cursor/rules/
```

Por ejemplo:

```
.cursor/
└── rules/
    ├── general.mdc
    ├── frontend.mdc
    ├── backend.mdc
    └── testing.mdc
```

---

## 14. Paso 11: Crea TASKS.md

Nunca le pidas a la IA que construya toda la aplicación en un solo mensaje.

Divide el proyecto en tareas.

```markdown
# Tareas

## Fase 1: Configuración
- [ ] Inicializar el proyecto
- [ ] Configurar TypeScript
- [ ] Configurar Tailwind
- [ ] Configurar Git

## Fase 2: Autenticación
- [ ] Crear página de registro
- [ ] Crear página de inicio de sesión
- [ ] Configurar autenticación
- [ ] Proteger el panel de control
- [ ] Probar la autenticación

## Fase 3: Notas
- [ ] Crear tabla en la base de datos
- [ ] Crear servicio de notas
- [ ] Crear interfaz de notas
- [ ] Crear formulario de notas
- [ ] Agregar funcionalidad de edición
- [ ] Agregar funcionalidad de eliminación
- [ ] Agregar pruebas
```

Luego trabaja así:

TAREA-001 → Implementar → Probar → Revisar → Marcar como completa → TAREA-002

---

## 15. Paso 12: Crea DECISIONS.md

Esto almacena decisiones técnicas importantes.

Ejemplo:

```markdown
# Decisiones de Arquitectura

## ADR-001
Decisión: Usar Supabase para la base de datos.
Razón: Ofrece PostgreSQL, autenticación y servicios de
backend sin necesidad de gestionar nuestra propia infraestructura.

## ADR-002
Decisión: Usar Next.js en lugar de React + Express.
Razón: La aplicación no requiere un backend separado
y queremos una aplicación full-stack unificada.
```

Esto evita que la IA cambie decisiones arquitectónicas de forma aleatoria más adelante.

---

## 16. Paso 13: Crea MEMORY.md

Piensa en esto como el estado actual del proyecto.

Ejemplo:

```markdown
# Memoria del Proyecto

## Estado actual
Autenticación completada.
Funcionalidad de notas en progreso.

## Completado
- Configuración del proyecto
- Configuración de Git
- Configuración de la base de datos
- Autenticación

## Tarea actual
TAREA-012

## Problemas conocidos
- La barra de navegación móvil necesita mejoras.
- El estado de carga de las notas está incompleto.

## Siguiente paso
Completar la creación de notas.
```

Una distinción útil es:

| Archivo | Contenido |
|---|---|
| DECISIONS.md | Decisiones permanentes |
| MEMORY.md | Estado actual del proyecto |

---

## 17. Paso 14: Crea TEST_PLAN.md

Define qué significa realmente "funcionar".

```markdown
# Plan de Pruebas

## Autenticación
- El usuario puede registrarse
- El usuario puede iniciar sesión
- Las credenciales inválidas muestran un error
- Los usuarios sin sesión no pueden acceder al panel

## Notas
- El usuario puede crear una nota
- El usuario puede editar una nota
- El usuario puede eliminar una nota
- El usuario no puede acceder a la nota de otro usuario

## Responsive
Probar en:
- 375px
- 768px
- 1440px
```

Esto se convierte en tu lista de verificación de pruebas más adelante.

---

## 18. Paso 15: Crea SECURITY.md

Para proyectos en producción:

```markdown
# Requisitos de Seguridad

## Autenticación
Las rutas privadas requieren autenticación.

## Autorización
Los usuarios solo pueden acceder a recursos que les pertenecen.

## Secretos
Nunca expongas secretos en el código del lado del cliente.

## Base de datos
Usa políticas de acceso apropiadas.

## Entrada
Valida toda la entrada del usuario.

## APIs
Valida el cuerpo y los parámetros de las solicitudes.

## Carga de archivos
Valida:
- Tipo de archivo
- Tamaño del archivo
- Nombre del archivo
```

La seguridad no debe agregarse cinco minutos antes del despliegue.

---

## 19. Paso 16: Crea .env.example

Nunca coloques claves de API reales dentro de tu código fuente.

En su lugar:

```
DATABASE_URL=
SUPABASE_URL=
SUPABASE_ANON_KEY=
OPENAI_API_KEY=
STRIPE_SECRET_KEY=
```

Luego tu entorno local contiene los valores reales:

```
.env.local
```

Tu repositorio debe contener:

```
.env.example
```

no tus secretos reales.

---

## 20. Paso 17: Dale Contexto del Proyecto a la IA

Ahora abre tu herramienta de IA para programar.

No digas inmediatamente:

"Construye mi aplicación."

Comienza con:

```
Lee los siguientes archivos antes de hacer cualquier cambio:

PRD.md
ARCHITECTURE.md
DESIGN.md
RULES.md
TASKS.md

No modifiques nada todavía.

Primero:
1. Comprende el producto.
2. Comprende la arquitectura.
3. Revisa el sistema de diseño.
4. Revisa las reglas de desarrollo.
5. Revisa las tareas actuales.
6. Identifica información faltante.
7. Explica el plan de implementación para TAREA-001.

No escribas código todavía.
```

Esto permite que la IA entienda el proyecto antes de tocarlo.

---

## 21. Paso 18: Construye una Funcionalidad a la Vez

Usa este flujo de trabajo:

Comprender → Planificar → Implementar → Probar → Revisar → Confirmar (commit)

Por ejemplo:

- TAREA-001: Crear página de registro
- TAREA-002: Implementar lógica de registro
- TAREA-003: Agregar validación
- TAREA-004: Agregar pruebas de autenticación

---

## 22. Paso 19: Usa Cortes Verticales (Vertical Slices)

En lugar de construir:

Todo el frontend → Todo el backend → Base de datos

Construye un flujo de usuario completo.

Ejemplo:

Registro → Inicio de sesión → Panel de control → Crear nota → Guardar nota → Mostrar nota

Luego:

Editar nota → Guardar → Mostrar nota actualizada

Luego:

Eliminar nota → Confirmar → Actualización en base de datos → Actualización de interfaz

Esto facilita mucho la depuración.

---

## 23. Paso 20: Usa un Prompt Estructurado

Un buen prompt de programación tiene seis partes:

CONTEXTO, TAREA, ARCHIVOS, RESTRICCIONES, CRITERIOS DE ACEPTACIÓN, PRUEBAS

Ejemplo:

```
CONTEXTO
Estamos construyendo una aplicación de notas para estudiantes.
Lee PRD.md, ARCHITECTURE.md y RULES.md.

TAREA
Implementar la creación de notas.

ARCHIVOS
Archivos relevantes:
src/features/notes/
src/services/
src/types/

RESTRICCIONES
- Sigue la arquitectura existente.
- Reutiliza componentes existentes.
- No crees una segunda capa de base de datos.
- No modifiques archivos no relacionados.
- Valida la entrada.

CRITERIOS DE ACEPTACIÓN
- Un usuario con sesión iniciada puede crear una nota.
- El título es obligatorio.
- El contenido es obligatorio.
- La entrada inválida muestra un error.
- La nota se guarda en la base de datos.
- La nueva nota aparece en la interfaz.

PRUEBAS
Agrega las pruebas apropiadas.
Ejecuta el linter.
Ejecuta la verificación de tipos.
Ejecuta las pruebas relevantes.
```

Después de la implementación, reporta:

1. Archivos modificados
2. Qué se implementó
3. Pruebas ejecutadas
4. Problemas pendientes

---

## 24. Paso 21: Nunca le Des a la IA Tareas Enormes

### Malo

"Construye toda la aplicación SaaS."

### Mejor

"Construye la autenticación."

### Óptimo

```
Crea la interfaz de registro.
No implementes la autenticación todavía.
Sigue DESIGN.md.

Requisitos:
- Campo de correo electrónico
- Campo de contraseña
- Campo de confirmar contraseña
- Validación
- Estado de carga
- Estado de error
- Responsive para móviles

No modifiques archivos no relacionados.
```

Las tareas pequeñas le dan a la IA menos margen para malinterpretar tu proyecto.

---

## 25. Paso 22: Prueba Cada Funcionalidad

Después de implementar una funcionalidad:

Código → Linter → Verificación de tipos → Pruebas unitarias → Pruebas de integración → Pruebas E2E

### Verificación de tipos

```
npm run typecheck
```

### Linter

```
npm run lint
```

### Pruebas

```
npm test
```

### Build (compilación)

```
npm run build
```

Tus comandos exactos dependen de la configuración del proyecto.

---

## 26. Paso 23: Usa Pruebas de Extremo a Extremo (E2E)

Las pruebas E2E verifican la aplicación desde la perspectiva del usuario.

Por ejemplo:

Abrir el sitio web → Registrarse → Iniciar sesión → Crear nota → Refrescar → Verificar que la nota existe → Editar nota → Eliminar nota → Cerrar sesión

Herramientas como Playwright son útiles para automatizar pruebas basadas en navegador.

---

## 27. Paso 24: Revisa el Código Generado por la IA

No asumas:

"Compiló, así que está correcto."

Pídele a la IA:

```
Revisa la implementación contra:
PRD.md
ARCHITECTURE.md
DESIGN.md
RULES.md
TEST_PLAN.md
SECURITY.md

Verifica:
- Corrección
- Arquitectura
- Seguridad
- Manejo de errores
- Accesibilidad
- Diseño responsive
- Rendimiento
- Duplicación de código

No modifiques nada todavía.
Reporta todos los problemas primero.
```

Luego corrígelos uno por uno.

---

## 28. Paso 25: Aprende a Depurar con IA

Cuando algo se rompe, no digas:

"Arréglalo."

Dale a la IA información estructurada.

```
ERROR
[pega el error]

COMPORTAMIENTO ESPERADO
El usuario debería ser redirigido al panel de control.

COMPORTAMIENTO ACTUAL
La página muestra un error 500.

PASOS PARA REPRODUCIR
1. Iniciar sesión
2. Hacer clic en Panel de control
3. Aparece el error

RESTRICCIÓN
No cambies el esquema de la base de datos.
```

Luego pregunta:

```
No modifiques código todavía.
Encuentra la causa raíz.

Explica:
1. ¿Qué está fallando?
2. ¿Por qué está fallando?
3. ¿Qué archivo es responsable?
4. ¿Cuál es la solución más pequeña?
5. ¿Cómo probaremos la solución?
```

Luego:

```
Implementa la solución más pequeña.
No refactorices código no relacionado.
Ejecuta las pruebas relevantes.
```

---

## 29. Paso 26: Usa Git Durante Todo el Desarrollo

Después de una funcionalidad que funciona:

```
git status
```

Luego:

```
git add .
```

Luego:

```
git commit -m "feat: agregar creación de notas"
```

Luego:

```
git push
```

Usa ramas (branches) para proyectos más grandes:

```
main
│
├── feature/auth
├── feature/notes
├── feature/search
└── fix/mobile-navbar
```

Esto protege tu código funcional de errores generados por la IA.

---

## 30. Paso 27: Prepárate para el Despliegue

Antes del despliegue, verifica:

### Funcionalidad

- [ ] Registro
- [ ] Inicio de sesión
- [ ] Cierre de sesión
- [ ] Operaciones CRUD
- [ ] Formularios
- [ ] Manejo de errores
- [ ] Estados de carga
- [ ] Estados vacíos

### Interfaz

- [ ] Móvil
- [ ] Tablet
- [ ] Escritorio
- [ ] Accesibilidad
- [ ] Navegación por teclado

### Seguridad

- [ ] Sin secretos en Git
- [ ] Autenticación verificada
- [ ] Autorización verificada
- [ ] Seguridad de base de datos configurada
- [ ] Validación de entrada
- [ ] Validación de API

### Código

- [ ] TypeScript pasa
- [ ] Linter pasa
- [ ] Pruebas pasan
- [ ] Build de producción pasa

---

## 31. Paso 28: Despliega Primero en Vista Previa (Preview)

Tu pipeline de despliegue debería verse así:

LOCAL → VISTA PREVIA → QA → PRODUCCIÓN

Nunca hagas de producción tu primer entorno de pruebas.

Por ejemplo:

feature/notes → Despliegue de vista previa → Probar → Corregir → Fusionar (merge) → Producción

---

## 32. Paso 29: Despliega a Producción

Para una aplicación Next.js, Vercel es una opción común de despliegue.

El flujo general es:

Repositorio de GitHub → Conectar a Vercel → Configurar variables de entorno → Desplegar → URL de vista previa → Probar → Producción

También puedes usar el CLI de Vercel cuando sea apropiado.

```
vercel
```

Después de probar:

```
vercel --prod
```

---

## 33. Paso 30: Configura las Variables de Entorno

Tu entorno local podría contener:

```
.env.local
```

Producción debe tener sus propios valores.

Por ejemplo:

| Entorno | Variable |
|---|---|
| Desarrollo | DATABASE_URL=development-db |
| Vista previa | DATABASE_URL=staging-db |
| Producción | DATABASE_URL=production-db |

No asumas que tu entorno local es idéntico al de producción.

---

## 34. Paso 31: QA de Producción

Después del despliegue, prueba la aplicación real en vivo.

No pruebes solo en localhost.

Verifica:

URL en vivo → Registro → Inicio de sesión → Funcionalidades principales → Operaciones de base de datos → Manejo de errores → Móvil → Escritorio

También prueba:

- Refrescar páginas
- URLs directas
- Acceso sin sesión iniciada
- Entradas inválidas
- Red lenta
- Base de datos vacía
- Credenciales incorrectas

---

## 35. Paso 32: Monitorea la Aplicación

El despliegue no es el final.

El ciclo de vida de producción es:

Desplegar → Monitorear → Recopilar retroalimentación → Encontrar errores → Corregir → Probar → Desplegar de nuevo

Considera agregar:

- Rastreo de errores
- Analítica
- Monitoreo de rendimiento
- Copias de seguridad de la base de datos
- Monitoreo de disponibilidad (uptime)

---

## 36. Paso 33: Mantén la Documentación del Proyecto

A medida que el proyecto cambia, actualiza:

- TASKS.md
- MEMORY.md
- DECISIONS.md
- README.md
- ARCHITECTURE.md

No dejes que la documentación describa una aplicación que ya no existe.

La IA necesita contexto preciso.

---

## 37. La Estructura de Proyecto Recomendada

Para un proyecto serio de principiante:

```
student-dashboard/
│
├── docs/
│ │
│ ├── PRD.md
│ ├── ARCHITECTURE.md
│ ├── DESIGN.md
│ ├── TEST_PLAN.md
│ ├── SECURITY.md
│ ├── DECISIONS.md
│ └── MEMORY.md
│
├── .cursor/
│ └── rules/
│ ├── general.mdc
│ ├── frontend.mdc
│ ├── backend.mdc
│ └── testing.mdc
│
├── src/
│ ├── app/
│ ├── components/
│ ├── features/
│ ├── services/
│ ├── lib/
│ ├── types/
│ └── utils/
│
├── tests/
│ ├── unit/
│ ├── integration/
│ └── e2e/
│
├── public/
│
├── .env.example
├── .gitignore
├── README.md
├── TASKS.md
├── package.json
└── ...
```

---

## 38. Qué Hace Cada Archivo

| Archivo | Propósito | Etapa |
| --- | --- | --- |
| PRD.md | ¿Qué estamos construyendo? | Planificación |
| ARCHITECTURE.md | ¿Cómo lo construiremos? | Planificación |
| DESIGN.md | ¿Cómo debería verse? | Planificación |
| RULES.md | ¿Cómo debería programar la IA? | Planificación |
| TASKS.md | ¿Qué deberíamos construir a continuación? | Desarrollo |
| DECISIONS.md | ¿Por qué tomamos esta decisión? | Desarrollo |
| MEMORY.md | ¿Cuál es el estado actual del proyecto? | Desarrollo |
| TEST_PLAN.md | ¿Cómo lo verificamos? | Pruebas |
| SECURITY.md | ¿Cómo lo protegemos? | Desarrollo |
| .env.example | ¿Qué configuración se requiere? | Configuración |
| README.md | ¿Cómo lo usan los humanos? | Documentación |

---

## 39. La Configuración Mínima para Principiantes

Si todo esto resulta abrumador, comienza solo con:

```
my-project/
│
├── PRD.md
├── RULES.md
├── TASKS.md
├── README.md
├── .env.example
│
└── src/
```

Luego agrega:

- ARCHITECTURE.md
- DESIGN.md
- TEST_PLAN.md
- SECURITY.md
- DECISIONS.md
- MEMORY.md

a medida que tu proyecto se vuelve más complejo.

---

## 40. El Ciclo Profesional de Vibe Coding

Para cada funcionalidad, sigue exactamente este ciclo:

1. LEER
2. COMPRENDER
3. PLANIFICAR
4. IMPLEMENTAR
5. PROBAR
6. REVISAR
7. CORREGIR
8. CONFIRMAR (COMMIT)
9. ACTUALIZAR LA DOCUMENTACIÓN

Luego pasa a la siguiente funcionalidad.

---

*Documento traducido al español a partir de la guía original "Vibe Coding: A Complete Beginner-to-Production Guide".*
