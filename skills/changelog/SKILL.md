---
name: changelog
description: >
  Mantenimiento del archivo CHANGELOG.md siguiendo el estándar Keep a Changelog.
  Trigger: Al registrar cambios de versión, nuevas funcionalidades, corrección de bugs o antes de un release.
license: Apache-2.0
metadata:
  author: D4KHO
  version: "1.0.0"
  scope: [root]
  auto_invoke:
    - "Add changelog entry for a PR or feature"
    - "Update CHANGELOG.md in any component"
    - "Review changelog format and conventions"
allowed-tools: Read, Edit, Write, Glob, Grep
---

<!-- ========================================================================= -->
<!-- ESTÁNDAR: Keep a Changelog (https://keepachangelog.com/es-ES/1.0.0/)      -->
<!-- FORMATO DE VERSIONES: SemVer (MAJOR.MINOR.PATCH)                          -->
<!-- ========================================================================= -->

## 1. Categorías Estándar

Al agregar cambios bajo una versión o bajo `[Unreleased]`, utiliza únicamente estas categorías:

- **`Added`**: Para nuevas funcionalidades.
- **`Changed`**: Para cambios en funcionalidades existentes.
- **`Deprecated`**: Para características que se eliminarán en próximas versiones.
- **`Removed`**: Para características eliminadas en este release.
- **`Fixed`**: Para corrección de errores.
- **`Security`**: Para vulnerabilidades resueltas.

---

## 2. Ejemplo de Entrada en CHANGELOG.md

```markdown
## [Unreleased]

### Added
- Soporte para autenticación de dos factores (2FA) vía TOTP.
- Endpoint de exportación de estadísticas en formato CSV (`/api/v1/metrics/export`).

### Fixed
- Corrección de condición de carrera en la actualización de balances de usuario (#89).
- Visualización truncada de gráficas en pantallas móviles menores a 640px.

### Changed
- Actualización de dependencias de seguridad de la API.
```
