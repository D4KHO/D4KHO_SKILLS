# Catálogo de Habilidades (Agent Skills)

Este directorio alberga las **Agent Skills** estructuradas bajo el estándar abierto [Agent Skills](https://agentskills.io). Proveen directrices de diseño, buenas prácticas y guardrails estrictos para asistentes de programación como Antigravity, Claude Code, Cursor, GitHub Copilot y OpenAI Codex.

---

## 🛠️ Configuración Inicial Rápida

Ejecuta el script de configuración para enlazar automáticamente las habilidades con tus herramientas de IA:

```bash
# Dar permisos de ejecución (en Linux/Mac/Git Bash)
chmod +x ./skills/setup.sh

# Configurar todos los asistentes soportados
./skills/setup.sh --all
```

Esto generará automáticamente los enlaces simbólicos esperados por cada herramienta:
- **Claude Code**: `.claude/skills/` y `CLAUDE.md`
- **Gemini CLI / Antigravity**: `.gemini/skills/` y `GEMINI.md`
- **OpenAI Codex**: `.codex/skills/` (lee nativamente `AGENTS.md`)
- **GitHub Copilot**: `.github/copilot-instructions.md` apuntando a `AGENTS.md`

---

## 📂 Directorio de Habilidades

```text
skills/
├── backend-api/            # Modelos, DTOs, autenticación, controladores y servicios
├── frontend-ui/            # Componentes, layout, design system y buenas prácticas UI
├── git-commit/             # Commits convencionales (Conventional Commits)
├── git-pr/                 # Creación y revisión de Pull Requests
├── changelog/              # Mantenimiento de CHANGELOG.md (Keep a Changelog)
├── mcp-server/             # Model Context Protocol (FastMCP)
├── test-api/               # Pruebas de integración y unitarias de API
├── test-ui/                # Pruebas E2E y de componentes con Playwright
├── typescript/             # Tipado estricto e interfaces
├── react-19/               # React 19 y React Compiler
├── nextjs-16/              # Next.js App Router y Server Actions
├── tailwind-4/             # Tailwind CSS v4 y helper cn()
├── playwright/             # Page Object Model y selectores semánticos
├── pytest/                 # Pruebas en Python
├── vitest/                 # Pruebas unitarias ultrarrápidas
├── tdd/                    # Flujo Test-Driven Development (Red-Green-Refactor)
├── zod-4/                  # Esquemas y validación de tipos
├── zustand-5/              # Estado global ligero
├── ai-sdk-5/               # Streaming y chat con Vercel AI SDK
├── django-drf/             # ViewSets, Serializers y Filters en Django
├── django-migration-psql/  # Migraciones sin downtime en PostgreSQL
├── postgresql-indexing/    # Optimización de consultas SQL
├── jsonapi/                # Estándar JSON:API v1.1
├── skill-creator/          # Generador de nuevas skills
├── skill-sync/             # Motor de sincronización automática de AGENTS.md
└── setup.sh                # Script de configuración multi-asistente
```

---

## 🔄 Sincronización Automática con `skill-sync`

Cada vez que agregues o edites una habilidad en `skills/`, actualiza automáticamente las tablas de invocación de los archivos `AGENTS.md`:

```bash
# Ejecutar sincronización
./skills/skill-sync/assets/sync.sh

# Modo simulación (Dry Run)
./skills/skill-sync/assets/sync.sh --dry-run
```
