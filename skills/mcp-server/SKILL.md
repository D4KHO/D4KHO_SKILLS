---
name: mcp-server
description: >
  Creación y mantenimiento de servidores Model Context Protocol (MCP) para conectar asistentes de IA con datos y herramientas locales.
  Trigger: Al desarrollar herramientas (Tools), recursos (Resources) o prompts de servidor MCP usando FastMCP / Python / TypeScript.
license: Apache-2.0
metadata:
  author: D4KHO
  version: "1.0.0"
  scope: [root, mcp_server]
  auto_invoke:
    - "Working on MCP server tools"
    - "Creating MCP tools, resources, or prompts"
    - "Configuring FastMCP server"
allowed-tools: Read, Edit, Write, Glob, Grep, Bash
---

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN: Librería MCP: FastMCP (Python) / @modelcontextprotocol/sdk -->
<!-- SERVIDOR LOCAL: mcp_server/                                               -->
<!-- PUERTO O TRANSPORTE: stdio / sse (Server-Sent Events)                      -->
<!-- ========================================================================= -->

## 1. Conceptos Fundamentales de MCP

1. **Tools**: Funciones ejecutables que el LLM puede llamar para realizar acciones (ej. consultar base de datos, ejecutar scripts).
2. **Resources**: Datos de solo lectura que el LLM puede consultar como contexto (ej. esquemas, logs, métricas).
3. **Prompts**: Plantillas de interacción parametrizadas para usuarios o agentes.

---

## 2. Ejemplo con FastMCP (Python)

```python
from mcp.server.fastmcp import FastMCP

# Inicializar servidor MCP
mcp = FastMCP("MiProyecto-MCP-Server")

@mcp.tool()
def get_system_health() -> dict:
    """Retorna el estado de salud y conectividad de la base de datos."""
    return {
        "status": "healthy",
        "database": "connected",
        "active_connections": 12
    }

@mcp.resource("schema://database")
def get_database_schema() -> str:
    """Expone el esquema actual de base de datos para contexto del agente."""
    return "table users (id uuid, email text, created_at timestamp);"

if __name__ == "__main__":
    mcp.run()
```
