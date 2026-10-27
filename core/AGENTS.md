# Core Engine & Business Logic - AI Agent Ruleset

> **Skills Reference**: Para patrones detallados, utiliza estas habilidades:
> - [`typescript`](../skills/typescript/SKILL.md) - Tipado estricto (si es JS/TS)
> - [`pytest`](../skills/pytest/SKILL.md) - Pruebas en Python (si es Python)
> - [`vitest`](../skills/vitest/SKILL.md) - Pruebas unitarias ultrarrápidas
> - [`tdd`](../skills/tdd/SKILL.md) - Test-Driven Development obligatorio para algoritmos y core
> - [`git-commit`](../skills/git-commit/SKILL.md) - Convención de commits

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN: Directorio de tu lógica de negocio pura o SDK              -->
<!-- LENGUAJE PRINCIPAL: TypeScript / Python / PHP / Go                        -->
<!-- RUTA LOCAL: core/ (o packages/core/ o lib/)                               -->
<!-- ========================================================================= -->

## Auto-invoke Skills

When performing these actions, ALWAYS invoke the corresponding skill FIRST:

| Action | Skill |
|--------|-------|
| Committing changes | `git-commit` |
| Creating a git commit | `git-commit` |
| Fixing bug | `tdd` |
| Implementing feature | `tdd` |
| Refactoring code | `tdd` |
| Writing Python tests with pytest | `pytest` |
| Writing TypeScript types/interfaces | `typescript` |
| Writing Vitest tests | `vitest` |

---

## CRITICAL RULES - NON-NEGOTIABLE

- **ALWAYS**: Mantener la lógica de negocio desacoplada de frameworks web o drivers de base de datos (Clean Architecture / Domain-Driven Design).
- **ALWAYS**: 100% de cobertura en tests unitarios para funciones de cálculo, parsing, hashing o transformaciones de datos.
- **NEVER**: Depender de variables globales mutables o efectos secundarios ocultos.
