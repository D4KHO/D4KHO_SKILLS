# Frontend UI - AI Agent Ruleset

> **Skills Reference**: Para patrones detallados, utiliza estas habilidades:
> - [`frontend-ui`](../skills/frontend-ui/SKILL.md) - Disciplina de componentes y diseño
> - [`test-ui`](../skills/test-ui/SKILL.md) - Pruebas E2E y de componentes (Playwright, Testing Library)
> - [`typescript`](../skills/typescript/SKILL.md) - Tipado estricto e interfaces
> - [`react-19`](../skills/react-19/SKILL.md) - Reglas React 19 y React Compiler (si aplica)
> - [`nextjs-16`](../skills/nextjs-16/SKILL.md) - App Router y Server Actions (si aplica)
> - [`tailwind-4`](../skills/tailwind-4/SKILL.md) - Clases de utilidad y helper cn()
> - [`zustand-5`](../skills/zustand-5/SKILL.md) - Estado global ligero
> - [`zod-4`](../skills/zod-4/SKILL.md) - Validación de esquemas en formularios
> - [`git-commit`](../skills/git-commit/SKILL.md) - Convenciones de commit
> - [`tdd`](../skills/tdd/SKILL.md) - Flujo Test-Driven Development

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN: Reemplaza estos placeholders según tu proyecto frontend     -->
<!-- URL BASE LOCAL: http://localhost:3000 (o 4200 Angular / 5173 Vite)        -->
<!-- URL PRODUCCIÓN: https://app.tu-dominio.com                                 -->
<!-- BIBLIOTECA BASE: components/ui/ (o components/shadcn/)                     -->
<!-- ========================================================================= -->

## Auto-invoke Skills

When performing these actions, ALWAYS invoke the corresponding skill FIRST:

| Action | Skill |
|--------|-------|
| App Router / Server Actions | `nextjs-16` |
| Committing changes | `git-commit` |
| Creating Zod schemas | `zod-4` |
| Creating a git commit | `git-commit` |
| Creating/modifying frontend UI components | `frontend-ui` |
| Fixing bug | `tdd` |
| Implementing feature | `tdd` |
| Refactoring code | `tdd` |
| Reviewing UI components and design system | `frontend-ui` |
| Structuring frontend layouts and state | `frontend-ui` |
| Using Zustand stores | `zustand-5` |
| Working with Tailwind classes | `tailwind-4` |
| Writing React components | `react-19` |
| Writing TypeScript types/interfaces | `typescript` |
| Writing component tests | `test-ui` |
| Writing frontend UI E2E tests | `test-ui` |

---

## CRITICAL RULES - NON-NEGOTIABLE

### Sistema de Diseño y Estilos
- **ALWAYS**: Reutilizar primero componentes primitivos base (`components/ui/` o `components/shadcn/`).
- **ALWAYS**: Emplear la utilidad `cn(...)` para combinar clases condicionales.
- **NEVER**: Escribir colores hexadecimales o valores arbitrarios dispersos (usar tokens semánticos del tema).

### Ámbito y Ubicación (Scope Rule)
- Usado en 2+ lugares $\rightarrow$ Mover a `components/shared/`, `hooks/` o `lib/`.
- Usado en 1 solo lugar $\rightarrow$ Mantener local en el directorio del feature.

---

## DECISION TREES

### Ubicación de Componentes
```text
¿Primitivo visual base reutilizable?      → components/ui/
¿Componente compartido entre páginas?     → components/shared/
¿Componente exclusivo de una sola vista?  → views/{modulo}/components/
```
