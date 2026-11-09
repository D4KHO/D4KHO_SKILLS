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

## Protocolo de Trabajo para Asistentes de IA (Modo Autónomo)

1. **Ruteo**: Determina qué componente o sub-agente es responsable de la tarea (`api/`, `ui/`, `core/`, etc.).
2. **Consulta de Skills**: Lee el `SKILL.md` pertinente antes de generar código o ejecutar cambios.
3. **Ejecución Proactiva e Inmediata (Autonomous Mode)**:
   - Ante solicitudes de revisión, optimización, auditoría o refactorización, **NUNCA** quedarse en diagnósticos puramente teóricos ni detenerse a pedir confirmación innecesaria ("¿Deseas que lo aplique?").
   - El agente DEBE asumir de inmediato el rol del Sub-Agente competente, editar los archivos en disco directamente aplicando los guardrails y verificar empíricamente.
4. **Verificación Físico-Empírica (Zero-Trust)**:
   - Comprobar sintaxis, tipos, linters y suites de pruebas reales antes de dar por cerrada la tarea.
5. **Entrega de Resultados & Separación de Canales (Artifacts vs. Chat)**:
   - **Para auditorías, análisis, diagnósticos o planes extensos:** La IA **DEBE** generar obligatoriamente un **Artifact Markdown (.md)** estructurado y entregar en el chat únicamente la ficha de identificación, el enlace al artifact y las decisiones clave (ver sección *Protocolo de Entrega de Auditorías y Artifacts*).
   - **Para modificaciones de código:** Entregar la lista de archivos modificados con enlaces navegables, comandos de prueba ejecutados y tabla de resultados.

---

## 🏷️ Formato Obligatorio de Respuestas (Identificación de Sub-Agente)

Toda respuesta técnica o reporte de intervención del asistente de IA en este repositorio **DEBE** comenzar obligatoriamente con la ficha de identificación del Sub-Agente activo para garantizar trazabilidad y transparencia visual:

```text
┌─────────────────────────────────────────────────────────┐
│ 🤖 SUB-AGENTE ACTIVO : [Backend API / Frontend UI / Core / Orquestador]
│ 📚 SKILL DE DOMINIO  : [backend-api / frontend-ui / typescript / etc.]
│ 📋 ARCHIVO DE REGLAS : [api/AGENTS.md / ui/AGENTS.md / core/AGENTS.md]
│ 🎯 FASE             : [Ejecución / Supervisión Zero-Trust / Resumen]
└─────────────────────────────────────────────────────────┘
```

> [!TIP]
> **Personalización para tu Proyecto:**
> - Puedes adaptar los nombres de los sub-agentes, las rutas de las reglas y las skills según la estructura real de tu repositorio (por ejemplo: si usas `backend/` y `frontend/`, ajusta `backend/AGENTS.md` y `frontend/AGENTS.md`).
> - Si prefieres respuestas más concisas sin cabecera visual, puedes remover o comentar esta sección en tu copia local.

---

## 📑 Protocolo de Entrega de Auditorías, Análisis y Planes (Artifacts Obligatorios)

> **PROPÓSITO UNIVERSAL**: Evitar la saturación del contexto y de la ventana de chat con reportes kilométricos. Separa el documento técnico profundo (Artifact interactivo/persistente) de la conversación ágil con el desarrollador (Chat ejecutivo).

Siempre que el usuario solicite un **análisis de arquitectura, auditoría de seguridad/código, diagnóstico de rendimiento, benchmark, comparativa tecnológica o plan de implementación extenso**:

### 1. 🚫 Regla de Oro: Prohibido volcar el análisis completo en el chat
La IA **NUNCA** debe imprimir un reporte extenso directamente en la ventana de conversación. Volcar párrafos y análisis largos en el chat degrada la experiencia del usuario, rompe la trazabilidad y satura la pantalla.

### 2. 📝 Creación Obligatoria de Artifact en Disco
La IA **DEBE invocar de inmediato la herramienta de escritura de archivos** para crear el reporte como un documento Markdown (`.md`):
- **En entornos con soporte nativo de Artifacts (Google Antigravity, Claude Code, Cursor):**
  - Escribir en la ruta del directorio de artifacts: `<appDataDir>/brain/<conversation-id>/nombre_reporte.md` pasando los metadatos correspondientes (`ArtifactMetadata: { UserFacing: true, RequestFeedback: false, Summary: "..." }`).
- **En entornos generales o sin directorio de conversación:**
  - Crear el archivo directamente en la carpeta de documentación del proyecto: `docs/analisis/nombre_reporte.md` o `.agents/reports/nombre_reporte.md`.

### 3. 📐 Estructura Estándar y Obligatoria del Artifact
Todo artifact técnico generado por el ecosistema debe estructurarse con la máxima calidad profesional:
1. **📌 Resumen Ejecutivo (Executive Summary):** Diagnóstico general en 1 o 2 párrafos y viabilidad del cambio.
2. **📊 Diagrama Visual (Mermaid):** Diagrama de flujo (`flowchart TD/LR`), secuencia o entidad-relación que ilustre el cuello de botella o la arquitectura propuesta.
3. **🔍 Hallazgos y Causas Raíz:** Desglose punto por punto con enlaces a los archivos físicos y fragmentos de código exactos.
4. **⚖️ Matriz de Priorización (Impacto vs. Esfuerzo):** Tabla comparativa con dificultad, riesgo, ganancia estimada y prioridad (🔴 Urgente / 🟡 Media / 🟢 Opcional).
5. **🛠️ Plan de Acción Accionable:** Pasos secuenciales de implementación con fragmentos de código de solución listos para aplicar.

### 4. 💬 Formato de Respuesta en Chat (Ultra-Resumido)
Tras generar el Artifact, la respuesta del asistente en el chat **DEBE limitarse estrictamente** a:
1. La **Ficha de Identificación de Sub-Agente** reglamentaria.
2. Un **enlace clicable directo** al artifact generado: `👉 [nombre_reporte.md](file:///ruta/absoluta/al/archivo.md)`.
3. Un **resumen ejecutivo de 3 a 5 viñetas** con los hallazgos principales.
4. Las **2 o 3 preguntas o decisiones clave** que requieren la aprobación del usuario para pasar a la acción.

### 5. ⚡ Cuándo NO Generar un Artifact (Respuestas Directas en Chat)
La IA **NUNCA debe crear ni modificar un Artifact** para interacciones cotidianas o preguntas puntuales:
- **Preguntas de navegación o ubicación:** Ejemplos: *"¿dónde está mi archivo .md?", "¿dónde configuro el puerto de la API?", "¿cómo se llama la función de login?"*.
- **Consultas breves o puntuales:** Preguntas conceptuales que se responden en 1 o 2 párrafos, sintaxis de comandos o dudas rápidas.
- **Consultas de estado y soporte:** Dudas sobre tests, errores de consola rápidos o confirmaciones de lectura.
- **Diálogo y clarificación:** Preguntas dirigidas al usuario solicitando aclaración de requisitos o aprobación.

👉 **En todos estos casos cotidianos**, la IA **DEBE responder de forma directa, ágil y concisa en el chat**, sin invocar herramientas de archivos ni crear artifacts innecesarios que ensucien el espacio de trabajo.

---

## 🛡️ Protocolo de Supervisión Zero-Trust (Verificación Empírica)

El Agente Orquestador Principal **NUNCA** debe confiar ciegamente en el reporte textual o afirmaciones de éxito de un sub-agente o herramienta. Debe asumir una postura de desconfianza por defecto y auditar el trabajo siguiendo estas reglas:

1. **Inspección de Cambios Físicos (Ground Truth):**
   - No dar por hecho que un archivo fue creado o modificado solo porque el asistente lo reporte textualmente.
   - Usar herramientas de inspección (`git diff`, lectura de archivos) para confirmar que los cambios existen físicamente en disco y que no hay sintaxis rota, código truncado ni marcadores de conflicto.

2. **Verificación Empírica Independiente (Build & Test Checks):**
   - **Frontend / UI:** Si el sub-agente afirma que la interfaz o componente está listo, ejecutar la compilación, linter o chequeo de tipos del proyecto (ej. `npm run build`, `pnpm type-check`, `yarn build`, `ng build`). Si el compilador o bundler arroja errores, el trabajo NO está terminado.
   - **Backend / API:** Comprobar la sintaxis, pruebas unitarias o linters del lenguaje (ej. `pytest`, `cargo check`, `go test`, `php -l`, `composer test`, `npm test`). Verificar que no existan imports rotos, variables indefinidas ni contratos de API inconsistentes.

3. **Auditoría de Guardrails de Skills:**
   - Comprobar que no se violaron las reglas estrictas `ALWAYS / NEVER` de las skills activas en el proyecto:
     - ❌ **Tipado débil:** Prohibir el uso injustificado de `any` o tipos dinámicos inseguros en lenguajes estáticos.
     - ❌ **Fugas de recursos:** Comprobar que streams, subscriptions, event listeners o conexiones a bases de datos se liberen adecuadamente.
     - ❌ **Bloqueo del hilo principal:** Tareas pesadas, llamadas a APIs externas lentas o I/O intensivo deben delegarse a workers, queues o background jobs.
     - ❌ **Mutaciones sin seguridad transaccional:** Operaciones críticas que modifiquen múltiples tablas o entidades deben estar protegidas con transacciones atómicas.

4. **Bucle de Auto-Corrección:**
   - Si la verificación empírica arroja fallas o advertencias bloqueantes, el asistente no debe trasladar el error al usuario como solución terminada; debe auto-corregir el código en disco y volver a ejecutar la verificación hasta obtener un estado verde/limpio.

---

## Directrices de Commits y Pull Requests

1. **Commits**: Formato Conventional Commits: `<tipo>(<scope>): <descripción>`.
   - Tipos: `feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `perf`, `style`.
2. **Pull Requests**:
   - Completar las secciones de Contexto, Descripción, Pasos para probar y Checklist.
   - Ejecutar linters y tests antes de solicitar revisión.
