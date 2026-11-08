# DDBus — Blueprint Técnico v1

## 1. Identidad del proyecto

**Nombre:** DDBus

**Empresa operadora:** Colectivos Ciudad de Ipiales S.A.

**Ciudad:** Ipiales, Nariño, Colombia

**Tipo de producto:** Aplicación móvil B2C para consulta del transporte urbano.

---

# 2. Objetivo

DDBus permitirá a los usuarios consultar información del servicio de transporte urbano operado por Colectivos Ciudad de Ipiales S.A.

La aplicación deberá permitir:

- Consultar rutas.
- Consultar paradas.
- Visualizar buses en un mapa.
- Visualizar la ubicación de los buses en tiempo real cuando exista información disponible.
- Consultar el estado de un bus.
- Consultar ocupación cuando exista información disponible.
- Consultar el recorrido de una ruta.
- Buscar rutas, paradas y destinos.
- Guardar rutas y paradas como favoritos.
- Recibir alertas relacionadas con el servicio.
- Reportar problemas.

La aplicación debe ser sencilla, rápida y fácil de entender.

---

# 3. Alcance inicial

DDBus cubrirá únicamente los servicios de:

**Colectivos Ciudad de Ipiales S.A.**

No se deben incorporar otros operadores de transporte al MVP.

El proyecto deberá diseñarse de manera que técnicamente pueda ampliarse en el futuro, pero esa ampliación no forma parte del alcance inicial.

---

# 4. Principios fundamentales

## 4.1 No inventar datos

El sistema nunca debe inventar:

- Rutas.
- Paradas.
- Buses.
- Horarios.
- Tarifas.
- Posiciones GPS.
- Ocupación.
- Alertas.
- Datos operativos.

Cuando los datos oficiales todavía no estén disponibles, se utilizarán datos claramente identificados como:

`DEMO`

o

`MOCK`

Nunca deberán presentarse datos de demostración como datos reales.

---

## 4.2 Arquitectura

La aplicación móvil nunca debe conectarse directamente a PostgreSQL.

Arquitectura:

```text
Flutter Mobile
       │
       │ HTTPS / WebSocket
       ▼
   NestJS API
       │
       ├──────────────► PostgreSQL + PostGIS
       │
       └──────────────► Redis
                              ▲
                              │
                         GPS Provider

Next.js Admin
       │
       ▼
   NestJS API