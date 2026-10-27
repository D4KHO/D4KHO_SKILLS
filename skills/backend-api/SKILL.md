---
name: backend-api
description: >
  Patrones arquitectónicos y buenas prácticas para el desarrollo de APIs Backend.
  Trigger: Al crear o modificar modelos de base de datos, endpoints, controladores, servicios, serializadores o capas de acceso a datos en la carpeta api/.
license: Apache-2.0
metadata:
  author: D4KHO
  version: "1.0.0"
  scope: [root, api]
  auto_invoke:
    - "Creating/modifying backend models, views, or endpoints"
    - "Designing API architecture and database access"
    - "Implementing backend business logic and services"
allowed-tools: Read, Edit, Write, Glob, Grep, Bash, WebFetch, WebSearch, Task
---

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN DEL PROYECTO: Personaliza estos valores según tu stack      -->
<!-- FRAMEWORK: Django REST Framework / Laravel / FastAPI / Express / NestJS    -->
<!-- URL BASE LOCAL: http://localhost:8000/api (o el puerto de tu backend)      -->
<!-- URL PRODUCCIÓN: https://api.tu-dominio.com/v1                             -->
<!-- BASE DE DATOS: PostgreSQL / MySQL / SQLite                                 -->
<!-- AUTENTICACIÓN: JWT / OAuth2 / API Key / Bearer Tokens                      -->
<!-- ========================================================================= -->

## 1. Reglas Críticas (ALWAYS vs NEVER)

### Modelos y Base de Datos
- **ALWAYS**: Usar UUIDv4 o identificadores opacos para llaves primarias en tablas expuestas externamente.
- **ALWAYS**: Incluir marcas de tiempo de auditoría (`created_at` / `inserted_at` y `updated_at`).
- **ALWAYS**: Si el sistema es Multi-Tenant, aislar las consultas por `tenant_id` (o mediante RLS / Scopes globales).
- **NEVER**: Exponer IDs secuenciales autoincrementales directamente a clientes públicos.
- **NEVER**: Ejecutar consultas SQL sin parametrizar (prevenir inyección SQL).

### Capa de Serialización / DTOs / Validación
- **ALWAYS**: Validar estrictamente las cargas útiles de entrada (`Payload`) antes de que toquen la lógica de negocio.
- **ALWAYS**: Separar esquemas/serializadores de lectura de los de creación y actualización (`ReadDTO`, `CreateDTO`, `UpdateDTO`).
- **NEVER**: Colocar lógica de negocio pesada o transaccional dentro del serializador o controlador.

### Controladores y Endpoints
- **ALWAYS**: Mantener los controladores delgados (*Thin Controllers, Fat Services*). Delegar la lógica compleja a servicios dedicados.
- **ALWAYS**: Retornar códigos de estado HTTP semánticos (`200 OK`, `201 Created`, `204 No Content`, `400 Bad Request`, `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, `422 Unprocessable Entity`).
- **ALWAYS**: Responder con estructuras de error estandarizadas (`{ "error": { "code": "...", "message": "...", "details": [] } }`).
- **NEVER**: Ejecutar operaciones bloqueantes de larga duración en el hilo HTTP principal (delegar a colas de tareas en segundo plano como Celery, Redis Queue, BullMQ o RabbitMQ).

---

## 2. Árboles de Decisión

### ¿Dónde colocar el código?
```text
¿Es validación de formato de datos?             → Serializer / DTO / Request Validator
¿Es orquestación HTTP y respuestas de estado?   → Controller / View / Endpoint Handler
¿Es regla de negocio o cálculo de dominio?     → Service / Use Case Layer
¿Es consulta compleja o reutilizable?          → Repository / Model QuerySet / Scope
¿Tarda más de 200ms o consulta servicio externo?→ Background Worker / Task Queue
```

---

## 3. Plantilla de Estructura de Endpoint Estándar

```text
POST /api/v1/{recurso}
Headers:
  Authorization: Bearer <token>
  Content-Type: application/json

Request Body:
{
  "name": "Ejemplo",
  "config": { ... }
}

Response (201 Created):
{
  "id": "uuid-v4-generado",
  "name": "Ejemplo",
  "created_at": "2026-10-27T12:00:00Z"
}
```
