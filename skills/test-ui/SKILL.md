---
name: test-ui
description: >
  Patrones para pruebas End-to-End (E2E) y pruebas de componentes en Frontend (Playwright, Cypress, Vitest, Testing Library).
  Trigger: Al crear o modificar pruebas de interfaz de usuario, flujos de navegación o tests de regresión visual en ui/ o frontend/.
license: Apache-2.0
metadata:
  author: D4KHO
  version: "1.0.0"
  scope: [root, ui]
  auto_invoke:
    - "Writing frontend UI E2E tests"
    - "Testing user interactions and flows"
    - "Writing component tests"
allowed-tools: Read, Edit, Write, Glob, Grep, Bash
---

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN: Herramienta de pruebas de UI                               -->
<!-- E2E: Playwright / Cypress                                                 -->
<!-- COMPONENTES / UNITARIOS: Vitest / Jest + React Testing Library            -->
<!-- URL BASE LOCAL: http://localhost:3000 (o 4200 / 5173)                     -->
<!-- ========================================================================= -->

## 1. Reglas Críticas (ALWAYS vs NEVER)

- **ALWAYS**: Usar selectores semánticos orientados al usuario (`getByRole`, `getByLabelText`, `getByPlaceholder`).
- **ALWAYS**: Implementar el patrón **Page Object Model (POM)** para centralizar selectores y acciones de vistas complejas.
- **NEVER**: Seleccionar elementos mediante selectores frágiles como XPath o clases CSS cosméticas generadas (`.css-1a2b3c`, `.sc-xyz`).
- **NEVER**: Usar esperas arbitrarias (`sleep(3000)` o `waitForTimeout(3000)`); utilizar esperas reactivas basadas en eventos o visibilidad (`expect(locator).toBeVisible()`).

---

## 2. Ejemplo con Playwright (Page Object Model)

```typescript
import { test, expect } from '@playwright/test';

test('Usuario inicia sesión exitosamente', async ({ page }) => {
  // Navegar a la vista
  await page.goto('/login');

  // Interactuar usando roles semánticos
  await page.getByLabel('Correo electrónico').fill('usuario@ejemplo.com');
  await page.getByLabel('Contraseña').fill('PasswordSeguro123!');
  await page.getByRole('button', { name: 'Iniciar Sesión' }).click();

  // Aserción orientada al resultado esperado
  await expect(page.getByRole('heading', { name: 'Panel Principal' })).toBeVisible();
});
```
