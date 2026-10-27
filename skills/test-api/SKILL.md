---
name: test-api
description: >
  Patrones para pruebas de integración y unitarias de APIs Backend (Pytest, PHPUnit, Jest, Supertest).
  Trigger: Al escribir o depurar pruebas para endpoints, servicios o modelos en la carpeta api/ o backend/.
license: Apache-2.0
metadata:
  author: D4KHO
  version: "1.0.0"
  scope: [root, api]
  auto_invoke:
    - "Writing backend API tests"
    - "Testing API endpoints and controllers"
    - "Testing database transactions and isolation"
allowed-tools: Read, Edit, Write, Glob, Grep, Bash
---

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN: Framework de pruebas del backend                           -->
<!-- HERRAMIENTA: Pytest / PHPUnit / Jest / Vitest / Supertest                 -->
<!-- COMANDO DE PRUEBAS: pytest api/tests / php artisan test / npm test        -->
<!-- ========================================================================= -->

## 1. Reglas Críticas (ALWAYS vs NEVER)

- **ALWAYS**: Aislar cada prueba en su propia transacción de base de datos o entorno efímero (rollback automático tras cada test).
- **ALWAYS**: Probar los 3 escenarios fundamentales de todo endpoint:
  1. **Happy Path**: Petición válida $\rightarrow$ Código `200` o `201`.
  2. **Validación**: Datos inválidos $\rightarrow$ Código `400` o `422`.
  3. **Seguridad / Permisos**: Sin autenticación o rol indebido $\rightarrow$ Código `401` o `403`.
- **ALWAYS**: Usar Mocks / Stubs para servicios externos de pago o APIs de terceros (Stripe, Twilio, AWS S3).
- **NEVER**: Depender del orden de ejecución de los tests (deben ser 100% deterministas e independientes).

---

## 2. Estructura de Test Típica (Arrange-Act-Assert)

```python
def test_create_resource_success(authenticated_client):
    # 1. Arrange: Preparar datos de entrada
    payload = {"name": "Test Resource", "is_active": True}
    
    # 2. Act: Ejecutar la petición HTTP
    response = authenticated_client.post("/api/v1/resources", json=payload)
    
    # 3. Assert: Verificar respuesta y persistencia
    assert response.status_code == 201
    assert response.json()["name"] == "Test Resource"
```
