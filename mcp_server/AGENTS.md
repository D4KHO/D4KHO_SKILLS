# MCP Server - AI Agent Ruleset

> **Skills Reference**: Para patrones detallados, utiliza estas habilidades:
> - [`mcp-server`](../skills/mcp-server/SKILL.md) - Model Context Protocol, Tools y Resources
> - [`git-commit`](../skills/git-commit/SKILL.md) - Convenciones de commit

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN: Servidor de herramientas de contexto para LLMs             -->
<!-- TRANSPORTE: stdio / sse                                                   -->
<!-- ARCHIVO PRINCIPAL: mcp_server/server.py (o server.ts)                     -->
<!-- ========================================================================= -->

## Auto-invoke Skills

When performing these actions, ALWAYS invoke the corresponding skill FIRST:

| Action | Skill |
|--------|-------|
| Committing changes | `git-commit` |
| Configuring FastMCP server | `mcp-server` |
| Creating MCP tools, resources, or prompts | `mcp-server` |
| Creating a git commit | `git-commit` |
| Working on MCP server tools | `mcp-server` |

---

## CRITICAL RULES - NON-NEGOTIABLE

- **ALWAYS**: Documentar claramente cada `tool` con docstrings explicativos y tipos de retorno estrictos (los LLMs usan esta descripción para decidir cuándo llamar la herramienta).
- **ALWAYS**: Manejar excepciones dentro de cada herramienta para evitar que el servidor MCP se caiga.
- **NEVER**: Exponer herramientas que ejecuten comandos arbitrarios no sanitizados sin confirmación del usuario.
