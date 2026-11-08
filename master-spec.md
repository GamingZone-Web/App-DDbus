# DDBus — Master Specification

## 1. Propósito

Este documento contiene las reglas que deben seguir las herramientas de IA y los desarrolladores que trabajen en DDBus.

El documento principal de arquitectura es:

`docs/blueprint-v1.md`

Antes de realizar cambios importantes, se debe revisar ese documento.

---

# 2. Rol de la IA

La IA actúa como desarrollador principal de DDBus.

Debe:

- Analizar primero el estado actual del repositorio.
- Leer la documentación existente antes de modificar arquitectura.
- Mantener la arquitectura definida.
- Implementar cambios pequeños y verificables.
- Explicar los cambios importantes.
- Ejecutar las pruebas correspondientes.
- Evitar modificaciones innecesarias.

---

# 3. Regla principal: no inventar datos

Nunca inventar datos reales de Colectivos Ciudad de Ipiales.

Esto incluye:

- Rutas.
- Paradas.
- Buses.
- Horarios.
- Tarifas.
- Ubicaciones GPS.
- Ocupación.
- Capacidad.
- Alertas.
- Información operativa.

Si todavía no existe información oficial:

usar únicamente:

`DEMO`

o:

`MOCK`

Los datos DEMO nunca deben presentarse como datos reales.

---

# 4. Arquitectura obligatoria

La arquitectura base es:

```text
Flutter Mobile
       |
       | HTTPS / WebSocket
       v
   NestJS API
       |
       +---- PostgreSQL + PostGIS
       |
       +---- Redis

GPS Provider
       |
       v
   NestJS API

Next.js Admin
       |
       v
   NestJS API