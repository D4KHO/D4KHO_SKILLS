# D4KHO_SKILLS 🚀
### Sistema Maestro de Agentes de IA, Sub-Agentes y Habilidades Modulares

Repositorio base y plantilla universal para estandarizar el desarrollo de software asistido por Inteligencia Artificial (Antigravity, Claude Code, Cursor, GitHub Copilot, OpenAI Codex) siguiendo el estándar abierto [Agent Skills](https://agentskills.io).

---

## 🎯 ¿Qué es D4KHO_SKILLS?

Este proyecto resuelve el problema de la **inconsistencia y alucinación** de los asistentes de IA al codificar:
1. **Orquestador Principal ([`AGENTS.md`](./AGENTS.md))**: Conoce la estructura completa del proyecto, sabe qué sub-agente tiene la responsabilidad de cada área y qué habilidades genéricas están disponibles.
2. **Sub-Agentes Especializados**: Cada módulo del proyecto (`api/`, `ui/`, `core/`, `mcp_server/`, `docs/`) tiene su propio [`AGENTS.md`](./api/AGENTS.md) con reglas no negociables (**ALWAYS / NEVER**) y árboles de decisión adaptados a su tecnología.
3. **Catálogo de Skills Reutilizables ([`skills/`](./skills/))**: Más de 20 habilidades empaquetadas que enseñan a la IA los estándares exactos de código (Next.js 16, React 19, TypeScript, Tailwind 4, Django, PostgreSQL, Playwright, TDD, Conventional Commits y más).
4. **Sincronización Automática ([`skill-sync`](./skills/skill-sync))**: Cada vez que se añade o modifica una skill, un script regenera automáticamente las tablas de invocación de los agentes.
5. **Supervisión Zero-Trust y Cabecera de Transparencia**: Validación empírica obligatoria en disco (compilación real, linters, tests) y ficha visual estándar que muestra qué sub-agente, skill y regla están activos en cada turno.
6. **Protocolo de Artifacts Automáticos (Separación de Canales)**: Desacopla las auditorías, diagnósticos de rendimiento y planes técnicos extensos del chat de conversación. La IA los escribe automáticamente en disco como Artifacts Markdown interactivos con diagramas Mermaid, entregando en el chat únicamente un resumen ejecutivo y las decisiones clave.

---

## 🏗️ Estructura del Repositorio

El repositorio está organizado con carpetas simuladas que representan la arquitectura típica de un proyecto fullstack profesional:

```text
D4KHO_SKILLS/
├── README.md               # [Este archivo] Guía completa del ecosistema
├── AGENTS.md               # [Orquestador Maestro] Reglas globales y mapa de delegación
├── api/                    # [Backend API]
│   ├── AGENTS.md           # Sub-Agente API: Modelos, DTOs, seguridad, transacciones
│   └── .gitkeep            # Carpeta lista para recibir tu código backend (Django, Laravel, etc.)
├── ui/                     # [Frontend UI]
│   ├── AGENTS.md           # Sub-Agente UI: Componentes, sistema de diseño, estado
│   └── .gitkeep            # Carpeta lista para recibir tu código frontend (Next.js, Angular, etc.)
├── core/                   # [Core / SDK / Lógica de Negocio]
│   ├── AGENTS.md           # Sub-Agente Core: Algoritmos puros, DDD, Clean Architecture
│   └── .gitkeep            # Carpeta lista para paquetes o bibliotecas del núcleo
├── mcp_server/             # [Model Context Protocol Server]
│   ├── AGENTS.md           # Sub-Agente MCP: Servidor FastMCP para exponer herramientas a LLMs
│   └── .gitkeep            # Carpeta lista para tus scripts y servidores MCP
├── docs/                   # [Documentación Técnica]
│   ├── AGENTS.md           # Sub-Agente Documentación: Markdown, guías y changelog
│   └── .gitkeep            # Carpeta lista para documentación técnica
└── skills/                 # [Directorio Central de Habilidades]
    ├── setup.sh            # Script para configurar symlinks con Claude, Gemini, Copilot
    ├── skill-sync/         # Motor que sincroniza los AGENTS.md con las skills
    ├── skill-creator/      # Guía y plantilla para crear nuevas skills
    ├── backend-api/        # Reglas para desarrollo de APIs
    ├── frontend-ui/        # Reglas para desarrollo de UI y componentes
    ├── git-commit/         # Conventional Commits estrictos
    ├── git-pr/             # Plantillas y checklist de Pull Requests
    ├── changelog/          # Mantenimiento Keep a Changelog
    ├── mcp-server/         # Patrones para servidores MCP
    ├── test-api/           # Pruebas de integración y unitarias de API
    ├── test-ui/            # Pruebas E2E y de componentes con Playwright
    ├── typescript/         # Tipado estricto e interfaces
    ├── react-19/           # React 19 y React Compiler
    ├── nextjs-16/          # App Router y Server Actions
    ├── tailwind-4/         # Estilos Tailwind v4 y utilidad cn()
    ├── playwright/         # Pruebas E2E con Page Object Model
    ├── pytest/             # Testing en Python
    ├── vitest/             # Unit testing ultrarrápido
    ├── tdd/                # Flujo Test-Driven Development
    ├── zod-4/              # Validación de esquemas
    ├── zustand-5/          # Estado global ligero
    ├── ai-sdk-5/           # Streaming y chat con Vercel AI SDK
    ├── django-drf/         # DRF ViewSets y Serializers
    ├── django-migration-psql/ # Migraciones seguras en PostgreSQL
    ├── postgresql-indexing/# Optimización de queries SQL
    └── jsonapi/            # Especificación JSON:API v1.1
```

---

## ⚙️ Cómo Personalizar los Placeholders en tu Proyecto

Cada archivo [`AGENTS.md`](./AGENTS.md) y [`SKILL.md`](./skills/) incluye un bloque de encabezado fácil de identificar para configurar tus rutas y variables. Por ejemplo:

```markdown
<!-- ========================================================================= -->
<!-- CONFIGURACIÓN DEL PROYECTO: Personaliza estos valores según tu stack      -->
<!-- NOMBRE DEL PROYECTO: Mi Proyecto                                          -->
<!-- URL BASE FRONTEND: http://localhost:3000 (o 4200 Angular / 5173 Vite)     -->
<!-- URL BASE BACKEND: http://localhost:8000/api (o 3001 / 5000)               -->
<!-- FRAMEWORK BACKEND: Laravel / Django / FastAPI / Express / NestJS          -->
<!-- FRAMEWORK FRONTEND: Angular / Next.js / React / Vue                       -->
<!-- ========================================================================= -->
```

Solo debes editar esas líneas iniciales para que el agente de IA conozca de inmediato tus puertos, endpoints y tecnologías activas.

---

## 🚀 Cómo Usar este Repositorio

### Opción 1: Usarlo como plantilla para un nuevo proyecto
1. Clona o copia esta carpeta para iniciar tu nuevo desarrollo.
2. Coloca tu código fuente dentro de las carpetas `api/`, `ui/`, etc.
3. Ejecuta la configuración de asistentes:
   ```bash
   chmod +x ./skills/setup.sh
   ./skills/setup.sh --all
   ```

### Opción 2: Incorporarlo a un proyecto existente (ej. MASIVO_WSP o Casa Bonita)
1. Copia la carpeta [`skills/`](./skills/) y el archivo [`AGENTS.md`](./AGENTS.md) a la raíz de tu proyecto.
2. Si tu proyecto tiene subcarpetas como `frontend/` y `backend/`, copia los respectivos `AGENTS.md` dentro de ellas (por ejemplo: `backend/AGENTS.md` usando la plantilla de `api/AGENTS.md`, y `frontend/AGENTS.md` usando la de `ui/AGENTS.md`).
3. Ejecuta `./skills/setup.sh --all`.

---

## 🔄 Flujo de Trabajo con los Agentes

1. **El Usuario hace una solicitud**:
   > *"Crea un nuevo endpoint para listar clientes con filtros por fecha."*
2. **El Agente Principal enruta la tarea**:
   - Lee [`AGENTS.md`](./AGENTS.md), detecta que la tarea pertenece a la API y activa el sub-agente [`api/AGENTS.md`](./api/AGENTS.md).
3. **El Sub-Agente carga las Skills requeridas**:
   - Revisa la tabla `Auto-invoke` y carga [`backend-api`](./skills/backend-api/SKILL.md).
   - Aplica las reglas obligatorias (`ALWAYS / NEVER`): UUIDv4 en PKs, timestamps de auditoría, controladores delgados y manejo unificado de errores.
4. **El Sub-Agente valida bajo Protocolo Zero-Trust y reporta**:
   - Inspecciona los archivos modificados físicamente en disco (`git diff`).
   - Ejecuta validación empírica real (compilador, linters, pruebas unitarias o de tipos).
   - Si detecta un error o regresión, ejecuta el bucle de auto-corrección antes de responder.
   - Presenta la respuesta encabezada con la ficha de identificación del Sub-Agente y el resumen de cambios.

---

## 📑 Protocolo de Artifacts Automáticos (Auditorías & Planes Técnicos)

Uno de los problemas más comunes al trabajar con asistentes de IA en tareas de ingeniería es que, al pedirles un análisis de rendimiento, seguridad o arquitectura, suelen volcar cientos de líneas de texto en la ventana de chat, saturando la pantalla y perdiendo persistencia.

D4KHO_SKILLS estandariza este comportamiento mediante una **regla no negociable en el Orquestador**:

```text
┌────────────────────────────────────────────────────────┐
│  SOLICITUD: "Analiza el rendimiento del proyecto..."   │
└───────────────────────────┬────────────────────────────┘
                            │
               ┌────────────┴────────────┐
               ▼                         ▼
   [ Artifact en Disco / Brain ]    [ Ventana de Chat ]
   ├── Resumen Ejecutivo            ├── Ficha de Sub-Agente Activo
   ├── Diagrama Mermaid             ├── Enlace directo clicable al Artifact
   ├── Tabla de Cuellos de Botella  └── 2-3 Decisiones Clave / Próximos Pasos
   ├── Matriz Impacto vs Esfuerzo
   └── Plan de Acción con Código
```

### ¿Cómo funciona en cualquier proyecto replicado?
Cuando el usuario solicita una auditoría o plan:
1. El agente de IA **detecta la intención** (análisis, auditoría, benchmark, diagnóstico).
2. **Crea automáticamente el Artifact** en el directorio persistente (`<appDataDir>/brain/<conversation-id>/nombre_reporte.md` en Antigravity / Claude Code, o en `docs/analisis/` en repositorios estándar).
3. **Mantiene el chat limpio y accionable:** En la conversación solo entrega la ficha del sub-agente, el link directo al archivo generado y las opciones que requieren autorización humana.

> [!NOTE]
> **¿Y con preguntas cotidianas o simples?**  
> Para preguntas normales (ej. *"¿dónde está mi archivo .md?", "¿cómo corro los tests?", "¿qué hace esta función?"*), la regla prohíbe crear artifacts. El asistente responde de forma **inmediata, directa y ágil en el chat** sin crear archivos innecesarios.

---

## 📋 Guía Rápida: Cómo Replicar esta Arquitectura en Cualquier Proyecto

Para llevar este ecosistema de sub-agentes, skills y artifacts a cualquier repositorio nuevo o existente (ej. un proyecto Laravel + Angular, FastAPI + React, Django + Vue, o Go + Flutter):

### Paso 1: Copiar el Orquestador Raíz
Copia [`AGENTS.md`](./AGENTS.md) a la raíz de tu nuevo proyecto y personaliza el bloque inicial de metadatos:
```markdown
<!-- NOMBRE DEL PROYECTO: Mi App Inmobiliaria                               -->
<!-- URL LOCAL BACKEND API: http://localhost:8000/api                        -->
<!-- URL LOCAL FRONTEND UI: http://localhost:4200                            -->
```

### Paso 2: Crear los Sub-Agentes por Directorio
Crea un archivo `AGENTS.md` dentro de cada carpeta principal del proyecto adaptado a sus tecnologías reales:
- Si tu backend está en `backend/`, crea `backend/AGENTS.md` con las reglas de tu framework y base de datos.
- Si tu frontend está en `frontend/`, crea `frontend/AGENTS.md` con las reglas de tus componentes y estado.
- *Tip*: Puedes usar como base las plantillas en [`api/AGENTS.md`](./api/AGENTS.md) y [`ui/AGENTS.md`](./ui/AGENTS.md).

### Paso 3: Copiar las Skills Necesarias
Copia la carpeta `skills/` (o crea un symlink) con las habilidades que aplican a tu stack (ej. `laravel-backend`, `angular-frontend`, `postgresql-indexing`, `tdd`, `git-commit`).

### Paso 4: ¡Listo! El Asistente de IA Actúa en Modo Autónomo
Cualquier agente moderno (Google Antigravity, Claude Code, Cursor, Copilot Workspace) leerá la jerarquía automáticamente y:
- Asumirá la identidad del sub-agente correcto con la ficha visual.
- Seguirá el protocolo Zero-Trust verificando en disco.
- Creará artifacts estructurados en análisis extensos sin saturar tu chat.

---

## ➕ Cómo Crear Nuevas Habilidades

Para agregar una nueva tecnología o estándar a tu catálogo:
1. Consulta la habilidad [`skill-creator`](./skills/skill-creator/SKILL.md).
2. Crea una nueva carpeta en `skills/{nombre-de-la-skill}/` con su archivo `SKILL.md`.
3. Define en el frontmatter YAML su nombre, descripción, alcance (`metadata.scope`) y acciones (`metadata.auto_invoke`).
4. Ejecuta la sincronización:
   ```bash
   ./skills/skill-sync/assets/sync.sh
   ```
   Esto insertará automáticamente la nueva skill en las tablas correspondientes de todos los archivos `AGENTS.md`.

---

## 📤 Subir a tu Repositorio de GitHub

Para guardar esta base maestra en tu perfil de GitHub:

```bash
# 1. Inicializar repositorio git
git init -b main

# 2. Agregar todos los archivos
git add .

# 3. Crear commit inicial
git commit -m "feat(skills): initial commit with master agents and skills architecture"

# 4. Vincular con tu repositorio remoto en GitHub
git remote add origin https://github.com/D4KHO/D4KHO_SKILLS.git

# 5. Subir a GitHub
git push -u origin main
```
