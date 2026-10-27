# Repository Guidelines & Master Agent Orchestrator

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN GENERAL DEL PROYECTO: Personaliza estas rutas y URLs         -->
<!-- NOMBRE DEL PROYECTO: Mi Proyecto Fullstack                                -->
<!-- URL DEL FRONTEND: http://localhost:3000 (o https://app.tu-dominio.com)    -->
<!-- URL DEL BACKEND API: http://localhost:8000/api (o https://api.tu-dominio) -->
<!-- REPOSITORIO GIT: https://github.com/tu-usuario/tu-repo                    -->
<!-- ========================================================================= -->

## Cómo Funciona este Ecosistema

- Este archivo [`AGENTS.md`](./AGENTS.md) es el **Orquestador Principal** para agentes de IA (Antigravity, Claude Code, Cursor, Copilot, Codex).
- Cada componente del proyecto cuenta con su propio subdirectorio y su **Sub-Agente especializado** con directrices locales (`api/AGENTS.md`, `ui/AGENTS.md`, etc.).
- **Regla de Precedencia**: Los lineamientos del Sub-Agente local sobrescriben a este archivo raíz en caso de conflicto dentro de su subdirectorio.
- **Flujo de Ejecución**:
  1. Si la tarea es general/transversal $\rightarrow$ El Agente Principal la resuelve con las **Skills Genéricas**.
  2. Si la tarea afecta a un componente $\rightarrow$ Se delega al **Sub-Agente** del subdirectorio correspondiente, el cual carga sus **Skills de Dominio predefinidas**, ejecuta las acciones bajo reglas estrictas `ALWAYS / NEVER`, y devuelve un resumen de resultados.

---

## Estructura de Componentes y Sub-Agentes

| Componente | Directorio | Sub-Agente | Stack Sugerido / Configurable |
| :--- | :--- | :--- | :--- |
| **Backend API** | [`api/`](./api) | [`api/AGENTS.md`](./api/AGENTS.md) | Django / Laravel / FastAPI / Express / NestJS |
| **Frontend UI** | [`ui/`](./ui) | [`ui/AGENTS.md`](./ui/AGENTS.md) | Next.js / React / Angular / Vue / Tailwind |
| **Core / Engine** | [`core/`](./core) | [`core/AGENTS.md`](./core/AGENTS.md) | Lógica de Negocio Pura, SDK, Domain-Driven |
| **MCP Server** | [`mcp_server/`](./mcp_server) | [`mcp_server/AGENTS.md`](./mcp_server/AGENTS.md) | FastMCP / Model Context Protocol |
| **Documentación** | [`docs/`](./docs) | [`docs/AGENTS.md`](./docs/AGENTS.md) | Markdown / MkDocs / Docusaurus |

---

## Catálogo de Habilidades (Available Skills)

### 1. Habilidades de Dominio (Project Domain Skills)

| Skill | Descripción | URL |
| :--- | :--- | :--- |
| `backend-api` | Arquitectura de API, modelos, DTOs, RLS y servicios | [SKILL.md](skills/backend-api/SKILL.md) |
| `frontend-ui` | Disciplina de componentes, layout, design system y estado | [SKILL.md](skills/frontend-ui/SKILL.md) |
| `git-commit` | Formato estricto Conventional Commits | [SKILL.md](skills/git-commit/SKILL.md) |
| `git-pr` | Flujo de Pull Requests, plantillas y checklists | [SKILL.md](skills/git-pr/SKILL.md) |
| `changelog` | Mantenimiento de CHANGELOG.md (Keep a Changelog) | [SKILL.md](skills/changelog/SKILL.md) |
| `mcp-server` | Creación de Tools y Resources para servidores MCP | [SKILL.md](skills/mcp-server/SKILL.md) |
| `test-api` | Pruebas de integración y unitarias para APIs | [SKILL.md](skills/test-api/SKILL.md) |
| `test-ui` | Pruebas E2E y de componentes (Playwright) | [SKILL.md](skills/test-ui/SKILL.md) |

### 2. Habilidades Genéricas (Generic Skills)

| Skill | Descripción | URL |
| :--- | :--- | :--- |
| `typescript` | Tipado estricto, const types, interfaces planas | [SKILL.md](skills/typescript/SKILL.md) |
| `react-19` | Patrones React 19, React Compiler (sin useMemo innecesario) | [SKILL.md](skills/react-19/SKILL.md) |
| `nextjs-16` | App Router, Server Actions, streaming | [SKILL.md](skills/nextjs-16/SKILL.md) |
| `tailwind-4` | Utilidad cn(), tokens y estilos modernos | [SKILL.md](skills/tailwind-4/SKILL.md) |
| `playwright` | Page Object Model, automatización web E2E | [SKILL.md](skills/playwright/SKILL.md) |
| `pytest` | Fixtures, mocking, parametrize en Python | [SKILL.md](skills/pytest/SKILL.md) |
| `vitest` | Unit testing ultrarrápido y React Testing Library | [SKILL.md](skills/vitest/SKILL.md) |
| `tdd` | Flujo Test-Driven Development (Red-Green-Refactor) | [SKILL.md](skills/tdd/SKILL.md) |
| `zod-4` | Validación de esquemas y DTOs | [SKILL.md](skills/zod-4/SKILL.md) |
| `zustand-5` | Manejo de estado ligero con persistencia | [SKILL.md](skills/zustand-5/SKILL.md) |
| `ai-sdk-5` | Integración con Vercel AI SDK para streaming y chat | [SKILL.md](skills/ai-sdk-5/SKILL.md) |
| `django-drf` | ViewSets, Serializers y Filters en Django | [SKILL.md](skills/django-drf/SKILL.md) |
| `django-migration-psql` | Migraciones seguras en PostgreSQL sin downtime | [SKILL.md](skills/django-migration-psql/SKILL.md) |
| `postgresql-indexing` | Optimización de queries e indexación SQL | [SKILL.md](skills/postgresql-indexing/SKILL.md) |
| `jsonapi` | Cumplimiento estricto de JSON:API v1.1 | [SKILL.md](skills/jsonapi/SKILL.md) |
| `skill-creator` | Creación de nuevas skills estandarizadas | [SKILL.md](skills/skill-creator/SKILL.md) |
| `skill-sync` | Sincronización automática de tablas Auto-invoke | [SKILL.md](skills/skill-sync/SKILL.md) |

---

## Auto-invoke Skills

Al realizar cualquiera de estas acciones, el agente de IA **DEBE invocar primero la skill correspondiente**:

| Action | Skill |
|--------|-------|
| Add changelog entry for a PR or feature | `changelog` |
| Adding indexes or constraints to database tables | `postgresql-indexing` |
| After creating/modifying a skill | `skill-sync` |
| App Router / Server Actions | `nextjs-16` |
| Building AI chat features | `ai-sdk-5` |
| Committing changes | `git-commit` |
| Configuring FastMCP server | `mcp-server` |
| Create PR that requires changelog entry | `changelog` |
| Create a PR with gh pr create | `git-pr` |
| Creating API endpoints | `backend-api` |
| Creating MCP tools, resources, or prompts | `mcp-server` |
| Creating ViewSets, serializers, or filters in api/ | `django-drf` |
| Creating Zod schemas | `zod-4` |
| Creating a git commit | `git-commit` |
| Creating new skills | `skill-creator` |
| Creating/modifying backend models, views, or endpoints | `backend-api` |
| Creating/modifying frontend UI components | `frontend-ui` |
| Designing API architecture and database access | `backend-api` |
| Fill pull request template and checklist | `git-pr` |
| Fixing bug | `tdd` |
| Implementing backend business logic and services | `backend-api` |
| Implementing feature | `tdd` |
| Modifying component | `tdd` |
| Preparing commit message | `git-commit` |
| Refactoring code | `tdd` |
| Regenerate AGENTS.md Auto-invoke tables (sync.sh) | `skill-sync` |
| Review PR requirements and templates | `git-pr` |
| Review changelog format and conventions | `changelog` |
| Reviewing UI components and design system | `frontend-ui` |
| Structuring frontend layouts and state | `frontend-ui` |
| Update CHANGELOG.md in any component | `changelog` |
| Using Zustand stores | `zustand-5` |
| Working on MCP server tools | `mcp-server` |
| Working with Tailwind classes | `tailwind-4` |
| Writing React components | `react-19` |
| Writing TypeScript types/interfaces | `typescript` |
| Writing Vitest tests | `vitest` |
| Writing backend API tests | `test-api` |
| Writing component tests | `test-ui` |
| Writing frontend UI E2E tests | `test-ui` |

---

## Directrices de Commits y Pull Requests

1. **Commits**: Formato Conventional Commits: `<tipo>(<scope>): <descripción>`.
   - Tipos: `feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `perf`, `style`.
2. **Pull Requests**:
   - Completar las secciones de Contexto, Descripción, Pasos para probar y Checklist.
   - Ejecutar linters y tests antes de solicitar revisión.
