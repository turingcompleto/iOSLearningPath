
# Proyectos iOS **sencillos y cero ambiguos** (MVVM + SwiftUI)

> Objetivo: darte **micro‑proyectos** de 1–2 días (o una tarde) que ejerciten *una sola cosa a la vez*. Cada uno trae alcance exacto, tareas por pasos y criterios de aceptación.

---

## 1) **Cronómetro con laps** (Concurrencia + Actors)
**Alcance**: 1 pantalla. Start/Stop/Reset y agregar laps. Persistencia **no** incluida.
**Stack**: SwiftUI + `actor` para estado del tiempo + `Task` para ticks.

**Tareas**
1. `TimeKeeper` (**actor**) con propiedades `isRunning`, `elapsed` y método `tick()` (cada 0.1 s).
2. `StopwatchViewModel` con acciones `start()`, `stop()`, `reset()`, `addLap()`.
3. `StopwatchView` con botones y lista de laps.
4. Prueba unitaria: lap añade el valor actual; reset vuelve a 0.

**Criterios de aceptación**
- [ ] Tick estable: el tiempo aumenta en ~0.1 s cuando está corriendo.
- [ ] `addLap` guarda el valor exacto del momento.
- [ ] `reset` limpia tiempo y laps.
- [ ] UI no se congela al iniciar/detener.

**Stretch (opcional)**: formateo mm:ss:cs, accesibilidad (VoiceOver), animación suave.

---

## 2) **HTTP Client Mini** (URLSession + Errores, sin servidor)
**Alcance**: 1 vista que hace **GET** a un **fixture local** (no internet) con `URLProtocol` mock.
**Stack**: SwiftUI + `URLSession` con `async/await` + `URLProtocol` custom.

**Tareas**
1. Define `HTTPClient` con `get(url:)` (genérico decodificando a `Decodable`).
2. Implementa `MockURLProtocol` que devuelve un JSON embebido.
3. `MiniListViewModel`: `load()` llama al cliente y expone `[Item]` + estados (`isLoading`, `error`).
4. Vista renderiza lista y estados vacíos/errores.

**Criterios de aceptación**
- [ ] Caso 200: muestra 5 ítems de fixture.
- [ ] Caso 500: muestra mensaje de error amigable.
- [ ] Timeout simulado: muestra retry y este funciona.
- [ ] Tests: 3 pruebas (200/500/timeout).

**Fixture sugerido** (`items.json`):
```json
[{"id":1,"title":"Alpha"},{"id":2,"title":"Beta"},{"id":3,"title":"Gamma"},{"id":4,"title":"Delta"},{"id":5,"title":"Epsilon"}]
```

---

## 3) **Lista→Detalle “Libros”** (SwiftUI Navegación)
**Alcance**: 2 pantallas (Lista y Detalle) + deep link `myapp://book/{id}` (simulado con `openURL`).

**Tareas**
1. Modelo `Book(id:Int,title:String,author:String,synopsis:String)`; dataset local (10 libros).
2. `BooksViewModel` con búsqueda (filter in‑memory) y selección.
3. `NavigationStack` con `NavigationPath` y ruta tipada a Detalle.
4. Implementa `onOpenURL` para navegar al detalle por id.

**Criterios de aceptación**
- [ ] Búsqueda filtra por título/autor en vivo.
- [ ] Deep link abre el libro correcto (simulado desde la app con un botón “Probar Deep Link”).
- [ ] Estado se restaura al volver desde Detalle.

**Stretch**: `ShareLink` en Detalle, Dynamic Type, etiquetas de accesibilidad.

---

## 4) **Design System Mini** (3 componentes reusables)
**Alcance**: 1 módulo `DesignSystem` con **3** componentes (Button, Card, Tag) + estilos y doc de uso.

**Tareas**
1. Define tokens (colores/tipografías/espaciados) en un `enum` o `struct`.
2. `DSButton(style:.primary|.secondary)`, `DSCard`, `DSTag(status:.info|.warning)`.
3. Playground/Screen “Catálogo” mostrando combinaciones.
4. Documenta en README cómo usar cada componente.

**Criterios de aceptación**
- [ ] Los 3 componentes se usan en otra vista de la app (no solo catálogo).
- [ ] Soporta modo claro/oscuro sin perder contraste AA.
- [ ] README con ejemplos de código y capturas.

---

## 5) **Notes Lite** (SwiftData CRUD básico)
**Alcance**: 1 entidad `Note(title, body, createdAt)` con lista + crear/editar/borrar. Sin sync ni cifrado.

**Tareas**
1. Modelo `@Model` y `@Query` en la lista.
2. Form de creación/edición con validación mínima (título no vacío).
3. Sort por `createdAt desc` y búsqueda local.
4. Test simple de inserción/edición (si usas store en memoria).

**Criterios de aceptación**
- [ ] Crear/editar/eliminar funcionan y la lista reacciona en vivo.
- [ ] Búsqueda por título funciona.
- [ ] Migración ligera: agrega campo `isPinned: Bool` con default `false` (opcional).

---

## 6) **Cache Wrapper** (Infra: memoria + disco)
**Alcance**: 1 wrapper `Cache<Key: Hashable, Value: Codable>` con TTL opcional + demo sencilla.

**Tareas**
1. Implementa capa en memoria (dictionary + fecha de expiración).
2. Persistencia en disco (archivo JSON por key o un único índice).
3. API: `set(_:for:ttl:)`, `get(_:)`, `invalidate(_:)`, `purgeExpired()`.
4. Vista simple con campos para `key`/`value` y botones `Set/Get/Invalidate`.

**Criterios de aceptación**
- [ ] TTL expira valores automáticamente en `get` y manualmente con `purgeExpired`.
- [ ] Tests para `set`/`get`/`expire`/`invalidate`.

---

## 7) **Chat Simulado** (WS mock sin servidor)
**Alcance**: 1 pantalla chat local con “online/offline”. Cuando está offline, mensajes se **encolan**; al volver online, se **envían**.

**Tareas**
1. `ChatService` con `PassthroughSubject` (o `AsyncStream`) simulando socket.
2. VM con estado `isOnline`, `queue:[Message]` y `send(_:)`.
3. UI con lista y input; toggle online/offline.
4. Métrica simple: tiempo desde encolado hasta entrega.

**Criterios de aceptación**
- [ ] En offline, mensajes quedan en cola y no aparecen como enviados.
- [ ] Al volver online, la cola se vacía en orden y aparecen como enviados.
- [ ] Indicador visual de estado (Tag DS).

---

## 8) **Notificaciones Locales + Deep Link**
**Alcance**: 1 demo que programa 3 categorías de notificación local. Al tocar, abre detalle `myapp://book/{id}`.

**Tareas**
1. Solicita permiso y define categorías/acciones.
2. Programa 3 notificaciones (5s, 10s, 15s) con payload que incluya `bookId`.
3. Maneja `userNotificationCenter(_:didReceive:)`/`onOpenURL` y navega al detalle.
4. Pantalla de “Historial” de notificaciones recibidas (en memoria).

**Criterios de aceptación**
- [ ] Acciones personalizadas aparecen.
- [ ] Tocar la noti abre el libro correcto.
- [ ] Historial muestra hora y `bookId` recibido.

---

## 9) **StoreKit 2 (Test local)** — *opcional y mínimo*
**Alcance**: 1 botón “Desbloquear Premium” usando **StoreKit Configuration** (sin backend).

**Tareas**
1. Crea un StoreKit Configuration con 1 producto no‑consumible `premium.unlock`.
2. VM con `isPremium` que se actualiza tras transacción.
3. Gating: vista premium vs. upsell.
4. Tests unitarios de lógica (envolviendo StoreKit en protocolo).

**Criterios de aceptación**
- [ ] Purchase simulado completa y cambia `isPremium`.
- [ ] Estado persiste en `UserDefaults` (simple).

---

## 10) **CI mínimo + Formato** (Infra)
**Alcance**: workflow de GitHub Actions que corre `xcodebuild test` y `swiftformat --lint`.

**Tareas**
1. Agrega `.github/workflows/ci.yml` con job en macOS-latest.
2. Instala `swiftformat`/`swiftlint` (si usas).
3. Falla el job si hay tests rotos o lint con errores.
4. Badge en README con estado del CI.

**Criterios de aceptación**
- [ ] PR bloqueado si falla CI.
- [ ] Badge visible con estado.

---

## Estructura base (para todos)
```
App/
  Application/
    AppMain.swift
    DIContainer.swift        // si aplica
  Features/
    <FeatureName>/
      UI/
      Presentation/          // ViewModel
      Domain/                // entidades/use cases (si aplica)
      Data/                  // mocks/protocols
  Core/
    DesignSystem/
    Networking/              // si aplica
    Persistence/             // si aplica
  Resources/
  Tests/
```

---

## Sugerencias de combinación (un fin de semana = 2–3 micros)
- **Combo 1:** (1) Cronómetro + (4) Design System + (10) CI → infra + UI base.
- **Combo 2:** (2) HTTP Mini + (3) Lista→Detalle + (8) Notis locales → features visibles sin backend real.
- **Combo 3:** (5) Notes Lite + (6) Cache Wrapper + (7) Chat simulado → persistencia + resiliencia.

---

## Qué subir a GitHub por micro‑proyecto
- README con: problema, decisión de diseño, métricas (si aplica), capturas y **TODOs**.
- 1–3 pruebas unitarias representativas.
- Etiqueta de release `v0.1` (tag) + changelog de 3 bullets.

---

## Rúbrica rápida para auto‑evaluarte (0–2 puntos c/u)
1. **Claridad del alcance** (0 ambiguo – 2 súper claro).
2. **Calidad del código** (0 spaghetti – 2 limpio, testable).
3. **Arquitectura** (0 acoplamiento – 2 límites claros).
4. **UX/Accesibilidad** (0 descuidada – 2 usable y accesible).
5. **Pruebas** (0 sin tests – 2 casos clave cubiertos).
6. **Documentación** (0 mínima – 2 README útil con decisiones).
7. **Métricas/Perf** (0 ninguna – 2 medición básica y mejora).

> 12+ puntos = listo para portafolio; 9–11 = casi; <9 = reintenta con un micro extra.
