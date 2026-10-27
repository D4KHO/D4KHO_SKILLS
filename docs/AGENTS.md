# Documentation - AI Agent Ruleset

> **Skills Reference**: Para patrones detallados, utiliza estas habilidades:
> - [`changelog`](../skills/changelog/SKILL.md) - Gestión de versiones y changelog
> - [`git-commit`](../skills/git-commit/SKILL.md) - Convención de commits

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN: Documentación técnica del proyecto                         -->
<!-- HERRAMIENTA: MkDocs / Docusaurus / Markdown puro                          -->
<!-- RUTA: docs/                                                               -->
<!-- ========================================================================= -->

## Auto-invoke Skills

When performing these actions, ALWAYS invoke the corresponding skill FIRST:

| Action | Skill |
|--------|-------|
| Add changelog entry for a PR or feature | `changelog` |
| Committing changes | `git-commit` |
| Creating a git commit | `git-commit` |
| Review changelog format and conventions | `changelog` |
| Update CHANGELOG.md in any component | `changelog` |

---

## CRITICAL RULES - NON-NEGOTIABLE

- **ALWAYS**: Redactar en formato Markdown estándar con enlaces relativos navegables.
- **ALWAYS**: Incluir bloques de código con resaltado de sintaxis especificado (````bash```, ````json```, etc.).
- **NEVER**: Dejar enlaces rotos o rutas absolutas de máquinas locales en la documentación pública.
