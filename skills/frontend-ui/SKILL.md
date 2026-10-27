---
name: frontend-ui
description: >
  Patrones de diseño, estructura de componentes y disciplina visual para aplicaciones Frontend.
  Trigger: Al crear o modificar componentes, layouts, hooks, estilos o estados en la carpeta ui/ o frontend/.
license: Apache-2.0
metadata:
  author: D4KHO
  version: "1.0.0"
  scope: [root, ui]
  auto_invoke:
    - "Creating/modifying frontend UI components"
    - "Reviewing UI components and design system"
    - "Structuring frontend layouts and state"
allowed-tools: Read, Edit, Write, Glob, Grep, Bash, WebFetch, WebSearch, Task
---

<!-- ========================================================================= -->
<!-- CONFIGURACIÓN DEL PROYECTO: Personaliza estos valores según tu frontend   -->
<!-- FRAMEWORK: Next.js / React / Angular / Vue / Svelte                       -->
<!-- URL BASE LOCAL: http://localhost:3000 (o 4200 para Angular / 5173 Vite)   -->
<!-- SISTEMA DE DISEÑO: shadcn/ui + Tailwind CSS / Vanilla CSS / Material      -->
<!-- GESTOR DE ESTADO: Zustand / React Context / Signals / Redux Toolkit       -->
<!-- CLIENTE HTTP: fetch nativo / Axios / TanStack Query (React Query)         -->
<!-- ========================================================================= -->

## 1. Disciplina de Sistema de Diseño (Design System Discipline)

El sistema de diseño y la paleta de componentes compartidos es la única fuente de verdad:
- **Reutilizar primero, nunca reinventar**: Antes de crear un botón, modal, dropdown o card, verifica si ya existe en la biblioteca compartida (`components/ui/` o `components/shadcn/`).
- **No inventar colores arbitrarios**: Emplea siempre los tokens semánticos del tema (`bg-background`, `text-primary`, `border-muted`, etc.). Prohibido usar colores hexadecimales quemados (`#1a2b3c`) dispersos en componentes.
- **Variantes semánticas**: Controla la apariencia mediante propiedades semánticas (`variant="destructive"`, `size="sm"`), no agregando clases visuales ad-hoc que rompan la consistencia.

---

## 2. Reglas Críticas (ALWAYS vs NEVER)

### Componentes y Estructura
- **ALWAYS**: Mantener componentes pequeños, puros y con una única responsabilidad.
- **ALWAYS**: Si un componente se usa en 2 o más lugares, moverlo a la carpeta de componentes compartidos (`components/shared/` o `components/common/`).
- **ALWAYS**: Si se usa en un solo lugar, mantenerlo co-localizado en la carpeta del feature correspondiente.
- **NEVER**: Mezclar peticiones directas a la API dentro del render visual del componente sin pasar por un servicio o hook de datos.

### Rendimiento y Estado
- **ALWAYS**: Separar componentes puramente visuales (*Dumb / Presentational*) de componentes contenedores con estado (*Smart / Container*).
- **ALWAYS**: En frameworks modernos como React 19 / Next.js, priorizar componentes del servidor (*Server Components*) y marcar con `"use client"` únicamente los nodos interactivos.
- **NEVER**: Almacenar en el estado global datos que pertenecen exclusivamente al estado local de un formulario o modal.

---

## 3. Árbol de Decisión: Ubicación de Código

```text
¿Es un primitivo visual base (Button, Input, Dialog)? → components/ui/ (o components/shadcn/)
¿Se usa en 2 o más vistas/dominios?                  → components/shared/
¿Pertenece exclusivamente a una vista/página?        → views/{modulo}/components/
¿Es lógica de estado global compartida?               → stores/ o state/
¿Es llamada a la API o transformación de DTO?        → services/ o api/
```
