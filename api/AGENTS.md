# Backend API - AI Agent Ruleset

> **Skills Reference**: Para patrones detallados, utiliza estas habilidades:
> - [`backend-api`](../skills/backend-api/SKILL.md) - Arquitectura de API, modelos, DTOs y servicios
> - [`test-api`](../skills/test-api/SKILL.md) - Pruebas automatizadas de endpoints y transacciones
> - [`django-drf`](../skills/django-drf/SKILL.md) - Patrones genéricos de DRF (si aplica)
> - [`postgresql-indexing`](../skills/postgresql-indexing/SKILL.md) - Optimización de queries e índices SQL
> - [`django-migration-psql`](../skills/django-migration-psql/SKILL.md) - Migraciones de base de datos seguras
> - [`git-commit`](../skills/git-commit/SKILL.md) - Convenciones de commit
> - [`tdd`](../skills/tdd/SKILL.md) - Flujo Test-Driven Development

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN: Reemplaza estos placeholders según tu proyecto backend      -->
<!-- URL BASE LOCAL: http://localhost:8000/api                                 -->
<!-- URL PRODUCCIÓN: https://api.tu-dominio.com                                -->
<!-- DIRECTORIO DE CÓDIGO: api/ (o backend/app/)                               -->
<!-- ========================================================================= -->

## Auto-invoke Skills

When performing these actions, ALWAYS invoke the corresponding skill FIRST:

| Action | Skill |
|--------|-------|
| Adding indexes or constraints to database tables | `postgresql-indexing` |
| Committing changes | `git-commit` |
| Creating a git commit | `git-commit` |
| Creating/modifying backend models, views, or endpoints | `backend-api` |
| Designing API architecture and database access | `backend-api` |
| Fixing bug | `tdd` |
| Implementing backend business logic and services | `backend-api` |
| Implementing feature | `tdd` |
| Refactoring code | `tdd` |
| Writing backend API tests | `test-api` |

---

## CRITICAL RULES - NON-NEGOTIABLE

### Arquitectura y Modelos
- **ALWAYS**: Modelos con marcas de tiempo `created_at` / `updated_at`.
- **ALWAYS**: Validación estricta en la capa de entrada (Requests / DTOs / Serializers).
- **NEVER**: Lógica pesada dentro de controladores/vistas (usar capa de servicios).
- **NEVER**: Dejar parámetros sin sanitizar en consultas a base de datos.

### Seguridad y Respuestas
- **ALWAYS**: Manejo de errores unificado en formato JSON.
- **NEVER**: Exponer trazas de error (stack traces) o credenciales en respuestas HTTP de producción.

---

## DECISION TREES

### Ubicación del Código
```text
¿Es validación de datos HTTP?            → DTO / Form Request / Serializer
¿Es respuesta y código HTTP?             → Controller / ViewSet
¿Es cálculo o lógica de negocio?        → Service / Use Case
¿Tarda más de 200ms o llama API externa? → Background Task Queue
```
