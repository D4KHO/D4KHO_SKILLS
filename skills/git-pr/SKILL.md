---
name: git-pr
description: >
  Estandariza la creación y revisión de Pull Requests (PR) en GitHub/GitLab.
  Trigger: Al redactar la descripción de un PR, revisar requerimientos previos a fusionar o preparar plantillas de PR.
license: Apache-2.0
metadata:
  author: D4KHO
  version: "1.0.0"
  scope: [root]
  auto_invoke:
    - "Create a PR with gh pr create"
    - "Review PR requirements and templates"
    - "Fill pull request template and checklist"
allowed-tools: Read, Edit, Write, Glob, Grep, Bash, WebFetch, WebSearch, Task
---

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN: URL de tu repositorio y rama principal                     -->
<!-- REPOSITORIO: https://github.com/tu-usuario/tu-repositorio                 -->
<!-- RAMA BASE: main (o master / develop)                                      -->
<!-- ========================================================================= -->

## 1. Proceso para Crear un PR Profesional

1. **Analizar los cambios completos**: Ejecutar `git diff main...HEAD` para entender el impacto total.
2. **Determinar los componentes afectados**: `api`, `ui`, `core`, `docs`, etc.
3. **Completar las secciones de la plantilla**:
   - **Contexto**: ¿Por qué se hace el cambio? Asociar el Issue (`Closes #123` o `Fixes #456`).
   - **Descripción**: Resumen claro de los componentes modificados.
   - **Pasos para Probar**: Instrucciones paso a paso para que el revisor reproduzca o valide el cambio.
   - **Checklist**: Verificación de linters, tests unitarios y documentación.
4. **Ejecutar la creación**: Usar GitHub CLI (`gh pr create`) o la interfaz web.

---

## 2. Plantilla Estándar de PR

```markdown
### 🎯 Contexto
<!-- Explica qué problema resuelve este PR o enlaza un issue existente -->
Resuelve el problema de validación de tokens de sesión expirados. Closes #42.

### 📝 Descripción
<!-- Resumen conciso de los cambios implementados -->
- Se agregó el middleware de renovación de token en el backend.
- Se implementó la captura de errores 401 en el cliente frontend.

### 🧪 Pasos para Revisar
<!-- Pasos reproducibles para verificar que todo funciona -->
1. Iniciar sesión con un usuario de prueba.
2. Forzar la expiración del token manipulando la fecha en DevTools.
3. Realizar una petición a `/api/recurso` y verificar que el token se renueva sin cerrar la sesión.

### ✅ Checklist
- [ ] Las pruebas automatizadas pasan exitosamente (`npm test` o `pytest`).
- [ ] No hay advertencias de linters ni errores de formateo.
- [ ] Se actualizó la documentación o el archivo `CHANGELOG.md` si aplica.
```
