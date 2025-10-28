# Calendario intensivo iOS — 10:00 a 17:00 con almuerzo (6 h netas aprox.)
_Inicio_: **Wednesday 29 Oct 2025**  ·  _Zona horaria_: America/Mexico_City

## Bloques diarios
- **Bloque 1**: 10:00–12:30 — Deep dive/lecturas + notas (2.5h)
- **Almuerzo**: 12:30–13:30 — break (1h)
- **Bloque 2**: 13:30–15:30 — Katas/POC (2h)
- **Bloque 3**: 15:30–17:00 — Implementación/Tests (1.5h)

> Consejo: usa 5–10 min al inicio de cada bloque para fijar objetivo, y 5 min al cierre para registrar learning/pendientes.


## Semana 1 — Swift moderno + Concurrencia

### Día 1 — Wednesday 29 Oct 2025
**Entregable:** Repo `concurrency-kata` con 6 tests verdes + ADR-001.md

**Bloque 1**
- Swift avanzado: protocolos con `associatedtype`, genéricos con constraints + `Codable` avanzado. Toma notas con ejemplos.

**Bloque 2**
- Katas: 3 funciones genéricas (map/flatMap custom, cache genérica in-memory con protocolo). Escribe tests.

**Bloque 3**
- Concurrencia 101: `async/await`, `Task`, `@MainActor`. Refactoriza una kata para ser async. Redacta ADR corto (decisiones).

**Criterios de aceptación**
- [ ] 6 tests unitarios pasan
- [ ] ADR describe 2 trade-offs
- [ ] Funciones documentadas en README

### Día 2 — Thursday 30 Oct 2025
**Entregable:** Bench simple + reporte en README

**Bloque 1**
- Aislamiento de datos: `Sendable`, `actor` y data races. Lectura + ejemplos mínimos.

**Bloque 2**
- POC: `CounterService` con `actor` + pruebas de race con `TaskGroup`.

**Bloque 3**
- Instrumenta (simple): mide tiempo promedio de 1000 ops concurrentes. Registra resultados.

**Criterios de aceptación**
- [ ] Actor evita race conditions
- [ ] Benchmark reproducible
- [ ] README con resultados

### Día 3 — Friday 31 Oct 2025
**Entregable:** Prefetcher + tests de cancelación

**Bloque 1**
- Structured concurrency: `TaskGroup`, cancelación, timeouts.

**Bloque 2**
- Implementa `ImagePrefetcher` (falso) con `TaskGroup` y cancelación.

**Bloque 3**
- Tests para cancelación/control de errores. Escribe ADR-002 (cancel policies).

**Criterios de aceptación**
- [ ] Cancelación interrumpe tareas hijas
- [ ] Cobertura > 70% en módulo prefetcher

### Día 4 — Monday 03 Nov 2025
**Entregable:** Guía interna de concurrencia.md

**Bloque 1**
- Errores en concurrencia: `throw`, `rethrow`, `Result`. Mapear a `DomainError`.

**Bloque 2**
- Refactor de Katas para propagar `DomainError` con tipado.

**Bloque 3**
- Checklist de buenas prácticas de concurrencia (propia) y ejemplos.

**Criterios de aceptación**
- [ ] Ejemplos compilables
- [ ] 3 anti‑patterns listados con alternativa

### Día 5 — Tuesday 04 Nov 2025
**Entregable:** Video demo + README-week1.md

**Bloque 1**
- Revisión semana: repaso notas y dudas.

**Bloque 2**
- Práctica cronometrada (45'): resolver 2 katas desde cero.

**Bloque 3**
- Demo grabada (5 min) + README con aprendizajes.

**Criterios de aceptación**
- [ ] Demo subido
- [ ] README con 5 aprendizajes
- [ ] 2 katas resueltas en <45' c/u

## Semana 2 — Networking HTTP + Manejo de errores

### Día 1 — Wednesday 05 Nov 2025
**Entregable:** MVP HTTPClient + tests básicos

**Bloque 1**
- Lectura: `URLSession` + políticas de ATS. Diseño del cliente HTTP (interfaces).

**Bloque 2**
- Implementa `HTTPClient` (GET/POST) con `async/await`, cabeceras y timeouts.

**Bloque 3**
- Tests con `URLProtocol` stub. Matriz de casos (200/400/500/timeout).

**Criterios de aceptación**
- [ ] Simula 4 escenarios
- [ ] 100% funciones públicas con tests

### Día 2 — Thursday 06 Nov 2025
**Entregable:** DTOs + mappers + ADR

**Bloque 1**
- Decodificación robusta: `Codable` con claves opcionales y `snake_case`.

**Bloque 2**
- POC: mapear 2 DTOs con fallbacks y valores por defecto.

**Bloque 3**
- Estrategia de `DomainError` + mapeos. ADR-003.

**Criterios de aceptación**
- [ ] Mappers probados con fixtures
- [ ] ADR con decisiones de defaulting

### Día 3 — Friday 07 Nov 2025
**Entregable:** HTTPClient v2 con retries

**Bloque 1**
- Retries exponenciales + cancelación.

**Bloque 2**
- Añade retries y política de reintentos al `HTTPClient`.

**Bloque 3**
- Tests de backoff y cancelación (con tiempos simulados).

**Criterios de aceptación**
- [ ] Backoff exponencial verificado
- [ ] Cancelación detiene retries

### Día 4 — Monday 10 Nov 2025
**Entregable:** Demo integración + README endpoints

**Bloque 1**
- Integración: consume un endpoint público (mock) y pinta JSON simple.

**Bloque 2**
- Paginación básica en cliente (query param `page`).

**Bloque 3**
- Documenta endpoints y ejemplos en README.

**Criterios de aceptación**
- [ ] Lista visible en simulador
- [ ] README con curl samples

### Día 5 — Tuesday 11 Nov 2025
**Entregable:** HTTPClient final + demo

**Bloque 1**
- Review semana + limpieza.

**Bloque 2**
- Refactor ligeros + mejorar tests.

**Bloque 3**
- Demo y resumen de aprendizajes.

**Criterios de aceptación**
- [ ] Todos los tests verdes
- [ ] Demo 5 min

## Semana 3 — SwiftUI avanzado + Navegación + Accesibilidad

### Día 1 — Wednesday 12 Nov 2025
**Entregable:** Lista filtrable + tests VM

**Bloque 1**
- Data flow en SwiftUI: `@StateObject`, Observation, `Environment`.

**Bloque 2**
- POC: vista Lista + filtro + `@Observable` VM.

**Bloque 3**
- Tests de VM con stubs de repo.

**Criterios de aceptación**
- [ ] Filtro reactivo funciona
- [ ] Tests cubren estados vacíos/errores

### Día 2 — Thursday 13 Nov 2025
**Entregable:** Navegación programática + deep-link

**Bloque 1**
- `NavigationStack/Path` + rutas tipadas + deep-links.

**Bloque 2**
- Implementa navegación a Detalle con `NavigationPath` y restauración.

**Bloque 3**
- Deep-link demo (`openURL`) + pruebas básicas.

**Criterios de aceptación**
- [ ] Path se restaura al relanzar
- [ ] Deep-link abre el item correcto

### Día 3 — Friday 14 Nov 2025
**Entregable:** Layout optimizado + métricas

**Bloque 1**
- Layout avanzado: `ViewThatFits`, `GeometryReader`, listas grandes.

**Bloque 2**
- Optimiza re-render con `@State` mínimo y `EquatableView`.

**Bloque 3**
- Medición simple de tiempo a primer render.

**Criterios de aceptación**
- [ ] Menos invalidaciones de vista
- [ ] Métrica comparativa en README

### Día 4 — Monday 17 Nov 2025
**Entregable:** A11y + i18n listo

**Bloque 1**
- Accesibilidad: labels, traits, Dynamic Type, contraste.

**Bloque 2**
- Audita la feature (VoiceOver) y corrige issues.

**Bloque 3**
- Localización básica (ES/EN) y formateo regional.

**Criterios de aceptación**
- [ ] VoiceOver anuncia correctamente
- [ ] Min. AA de contraste
- [ ] Localización sin strings sueltos

### Día 5 — Tuesday 18 Nov 2025
**Entregable:** CountriesApp v2 lista para semana 4

**Bloque 1**
- Review + pulido visual (Design System básico).

**Bloque 2**
- Snapshot tests opcionales de 2 pantallas.

**Bloque 3**
- Demo semanal.

**Criterios de aceptación**
- [ ] 2 snapshots estables
- [ ] Demo 5 min

## Semana 4 — Arquitectura (MVVM + Clean) + SPM + Design System

### Día 1 — Wednesday 19 Nov 2025
**Entregable:** Módulos SPM + pipeline mínimo

**Bloque 1**
- Define capas: Domain/Data/UI. Diagrama C4.

**Bloque 2**
- Crea módulos SPM: `Networking`, `Persistence`, `DesignSystem`.

**Bloque 3**
- Integra CI básico (build + test).

**Criterios de aceptación**
- [ ] Targets compilan
- [ ] Job CI pasa en PR

### Día 2 — Thursday 20 Nov 2025
**Entregable:** Dominio con cobertura alta

**Bloque 1**
- Use Cases + repositorios (protocolos) + mappers.

**Bloque 2**
- Implementa 2 casos de uso con stubs/mocks.

**Bloque 3**
- Tests de dominio al 80% cobertura.

**Criterios de aceptación**
- [ ] Cobertura >= 80% en Domain
- [ ] Sin dependencias UI en Domain

### Día 3 — Friday 21 Nov 2025
**Entregable:** DesignSystem v1 + docs

**Bloque 1**
- Design System: color, tipografía, 3 componentes reutilizables.

**Bloque 2**
- Integra DS en la feature previa.

**Bloque 3**
- Documenta catálogo de componentes.

**Criterios de aceptación**
- [ ] 3 componentes consumidos en app
- [ ] Docs con ejemplos

### Día 4 — Monday 24 Nov 2025
**Entregable:** DI Container + configs

**Bloque 1**
- DI Container (constructor injection), no singletons globales.

**Bloque 2**
- Wiring de app por entornos (dev/staging/prod).

**Bloque 3**
- ADR-004 con trade-offs.

**Criterios de aceptación**
- [ ] Swap de implementaciones por entorno
- [ ] ADR con riesgos

### Día 5 — Tuesday 25 Nov 2025
**Entregable:** Arquitectura v1 estable

**Bloque 1**
- Review + pulido + demo.

**Bloque 2**
- Checklist de calidad por feature.

**Bloque 3**
- Plan de mejoras semana 5.

**Criterios de aceptación**
- [ ] Pipeline verde
- [ ] Checklist completo

## Semana 5 — Persistencia (SwiftData) + Offline‑First + Keychain

### Día 1 — Wednesday 26 Nov 2025
**Entregable:** Modelo SwiftData + tests

**Bloque 1**
- SwiftData: modelado, relaciones, migraciones ligeras.

**Bloque 2**
- Implementa modelos + @Query + políticas de merge.

**Bloque 3**
- Tests de repos con store en memoria.

**Criterios de aceptación**
- [ ] Migración ligera validada
- [ ] Consultas con @Query funcionan

### Día 2 — Thursday 27 Nov 2025
**Entregable:** Capa de cache + sync inicial

**Bloque 1**
- Cache híbrido (memoria+disco) + invalidación.

**Bloque 2**
- Sincronización inicial offline‑first.

**Bloque 3**
- Pruebas de integración de sincronización.

**Criterios de aceptación**
- [ ] Latency menor en cache hit
- [ ] Sincroniza al volver la red

### Día 3 — Friday 28 Nov 2025
**Entregable:** AuthStorage + checklist seguridad

**Bloque 1**
- Keychain para tokens; Secure Enclave si aplica.

**Bloque 2**
- Abstracción de credenciales + rotación de tokens.

**Bloque 3**
- Pentest básico (checklist).

**Criterios de aceptación**
- [ ] Tokens solo en Keychain
- [ ] Checklist con 0 hallazgos críticos

### Día 4 — Monday 01 Dec 2025
**Entregable:** Demo offline‑first

**Bloque 1**
- E2E: flujo completo offline‑first (listar/guardar/refresh).

**Bloque 2**
- Métricas simples (fallos/sync time).

**Bloque 3**
- Documenta estrategia y riesgos.

**Criterios de aceptación**
- [ ] Flujo robusto sin red
- [ ] README con métricas

### Día 5 — Tuesday 02 Dec 2025
**Entregable:** Persistencia estable

**Bloque 1**
- Review + pulido + demo.

**Bloque 2**
- Refactor de queries lentas.

**Bloque 3**
- Plan para semana 6.

**Criterios de aceptación**
- [ ] Sin leaks, tiempos medidos
- [ ] Demo 5 min

## Semana 6 — WebSockets + Notificaciones + Testing + Performance + CI/CD

### Día 1 — Wednesday 03 Dec 2025
**Entregable:** WS client con resiliencia

**Bloque 1**
- WebSockets: reconexión, pings, backoff.

**Bloque 2**
- POC cliente WS con ecos (mock).

**Bloque 3**
- Colas locales + reintentos.

**Criterios de aceptación**
- [ ] Reconecta con backoff
- [ ] Mensajes encolados offline

### Día 2 — Thursday 04 Dec 2025
**Entregable:** Push demo + docs

**Bloque 1**
- Push notifications: categorías + deep‑link.

**Bloque 2**
- Demo local (UNUserNotificationCenter) + JSON payloads.

**Bloque 3**
- Docs de integración servidor.

**Criterios de aceptación**
- [ ] Deep‑link al hilo correcto
- [ ] Docs claros para backend

### Día 3 — Friday 05 Dec 2025
**Entregable:** Test suite consolidada

**Bloque 1**
- XCTest + XCUITest para flujos críticos.

**Bloque 2**
- Snapshot opcional de 2 pantallas clave.

**Bloque 3**
- Reporte de cobertura y flakiness.

**Criterios de aceptación**
- [ ] Cobertura domain >=80%
- [ ] 2 XCUITests estables

### Día 4 — Monday 08 Dec 2025
**Entregable:** Performance report

**Bloque 1**
- Instruments: Time Profiler/Allocations/Leaks.

**Bloque 2**
- Optimiza hot paths (SwiftUI state/layout).

**Bloque 3**
- Reporte antes/después con % mejora.

**Criterios de aceptación**
- [ ] >=20% mejora en un caso
- [ ] Sin fugas detectadas

### Día 5 — Tuesday 09 Dec 2025
**Entregable:** Build en TestFlight + case study

**Bloque 1**
- CI/CD: Fastlane beta lane + Actions/Xcode Cloud.

**Bloque 2**
- Sube a TestFlight con notas.

**Bloque 3**
- Retro final + README capstone.

**Criterios de aceptación**
- [ ] Build disponible en TF
- [ ] README con decisiones y métricas
