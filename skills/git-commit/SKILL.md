---
name: git-commit
description: >
  Genera mensajes de commit profesionales siguiendo la convención estándar Conventional Commits.
  Trigger: Al crear commits, después de finalizar cambios de código o cuando el usuario solicita hacer un commit.
license: Apache-2.0
metadata:
  author: D4KHO
  version: "1.0.0"
  scope: [root, api, ui, core, mcp_server]
  auto_invoke:
    - "Creating a git commit"
    - "Committing changes"
    - "Preparing commit message"
allowed-tools: Read, Edit, Write, Glob, Grep, Bash
---

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN: Ajusta los scopes habituales según los módulos de tu repo  -->
<!-- SCOPES TÍPICOS: api, ui, core, mcp, docs, config, auth, metrics           -->
<!-- ========================================================================= -->

## 1. Reglas Críticas (ALWAYS vs NEVER)

- **ALWAYS**: Usar el formato estricto de Conventional Commits: `<type>(<scope>): <descripción>`
- **ALWAYS**: Mantener la primera línea por debajo de los 72 caracteres.
- **ALWAYS**: Escribir en tiempo imperativo presente ("add feature", no "added feature").
- **ALWAYS**: Pedir confirmación al usuario antes de ejecutar el comando de commit en la terminal.
- **NEVER**: Incluir detalles minuciosos irrelevantes (evitar "edited 3 files and 14 lines").
- **NEVER**: Usar banderas destructivas como `git push --force` o `git push -f`.
- **NEVER**: Proponer commits de manera intrusiva si el usuario no ha solicitado guardar los cambios.

---

## 2. Tipos de Commits Permitidos

| Tipo | Cuándo Usarlo |
| :--- | :--- |
| `feat` | Nueva funcionalidad para el usuario final |
| `fix` | Corrección de un bug o error |
| `docs` | Cambios únicamente en documentación o README |
| `refactor` | Reestructuración de código sin alterar comportamiento |
| `test` | Incorporación o corrección de pruebas automatizadas |
| `chore` | Tareas de mantenimiento, dependencias o configuración |
| `perf` | Mejora medible de rendimiento o consumo de recursos |
| `style` | Formato, espacios, punto y coma (sin cambio de código) |

---

## 3. Ejemplo Estructurado

```text
feat(auth): add refresh token rotation mechanism

- Implement sliding window session expiration in backend
- Add interceptor for 401 automatic token renewal in frontend
- Update user session documentation
```
