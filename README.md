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
4. **El Sub-Agente valida y reporta**:
   - Aplica TDD creando o ejecutando los tests correspondientes.
   - Devuelve un informe estructurado de cambios al Agente Principal para entregártelo de forma clara y limpia.

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
