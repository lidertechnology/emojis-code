# 🎨 Angular L10 — Visual Code Conventions

> **Sistema de iconografía semántica** para comentarios de código en proyectos Angular.  
> Cada símbolo comunica la **intención** del elemento antes de leerlo.

---

## ¿Por qué usar esta convención?

En equipos grandes o proyectos complejos, el tiempo de comprensión del código es crítico. Esta iconografía permite:

- **Escaneo visual instantáneo** — identifica el tipo de elemento en un vistazo
- **Semántica uniforme** — todo el equipo habla el mismo "idioma visual"
- **Documentación implícita** — el emoji es el comentario más corto posible
- **Alineación izquierda** — siempre antes de `const`, `readonly` o definiciones

---

## 📐 Formato de uso

```ts
/* 📡 */ const contador = signal(0);
/* 💻 */ readonly total = computed(() => this.contador() * 2);
/* 🚀 */ readonly logger = effect(() => console.log(this.contador()));
```

El comentario va en la **misma línea**, pegado a la izquierda, antes de la declaración.

---

## 1 · Reactividad y Estado · Signals

| Emoji | Nombre | Uso |
|-------|--------|-----|
| `/* ✅ */` | **Simple Signal** | Booleanos y flags de estado |
| `/* 📡 */` | **Writable Signal** | Estado general de escritura |
| `/* 🛡️ */` | **Read-only Signal** | Protegido con `.asReadonly()` |
| `/* 💻 */` | **Computed** | Estado derivado, calculado |
| `/* 🚀 */` | **Effect** | Lanzadores y efectos secundarios |

```ts
/* ✅ */ const isVisible = signal(false);
/* 📡 */ const userName   = signal('');
/* 🛡️ */ readonly count  = this._count.asReadonly();
/* 💻 */ readonly label   = computed(() => `Hola, ${this.userName()}`);
/* 🚀 */ readonly tracker = effect(() => analytics.track(this.count()));
```

---

## 2 · Comunicación de Componentes

| Emoji | Nombre | Uso |
|-------|--------|-----|
| `/* ⤵️ */` | **Input** | Entrada de datos · *Data Down* |
| `/* ⤴️ */` | **Output** | Salida de eventos · *Event Up* |
| `/* ↔️ */` | **Model** | Binding bidireccional |

```ts
/* ⤵️ */ readonly title   = input.required<string>();
/* ⤴️ */ readonly clicked = output<void>();
/* ↔️ */ readonly value   = model('');
```

---

## 3 · Flujos Asíncronos · RxJS

| Emoji | Nombre | Uso |
|-------|--------|-----|
| `/* 👁️ */` | **Stream / Observable** | Observables puros de RxJS |

```ts
/* 👁️ */ readonly data$ = this.http.get<Item[]>('/api/items');
/* 👁️ */ readonly route$ = this.router.events.pipe(
            filter(e => e instanceof NavigationEnd)
          );
```

---

## 4 · Infraestructura y Lógica

| Emoji | Nombre | Uso |
|-------|--------|-----|
| `/* 💉 */` | **Inject** | Inyección de dependencias |
| `/* 🔘 */` | **Const** | Constantes inmutables |
| `/* 📝 */` | **Forms** | `FormGroup` / formularios reactivos |
/* `🧭` */ | **Router** | Navegación y rutas |

```ts
/* 💉 */ private readonly http    = inject(HttpClient);
/* 💉 */ private readonly router  = inject(Router);
/* 🔘 */ const MAX_RETRIES        = 3;
/* 📝 */ readonly form            = new FormGroup({ ... });
/* 🧭 */ readonly activeRoute     = inject(ActivatedRoute);
```

---

## 5 · Definiciones y Estructura

| Emoji | Nombre | Uso |
|-------|--------|-----|
| `/* 🧩 */` | **Interface** | Contratos de datos y modelos |
| `/* 🔢 */` | **Enum** | Diccionarios numéricos o estáticos |
| `/* 🏷️ */` | **DOM Reference** | `viewChild` / referencias HTML |

```ts
/* 🧩 */ interface User {
  id: number;
  name: string;
}

/* 🔢 */ enum Status {
  Active = 'ACTIVE',
  Inactive = 'INACTIVE',
}

/* 🏷️ */ readonly inputRef = viewChild<ElementRef>('myInput');
```

---

## 🗺️ Referencia rápida — Cheat Sheet

```
SIGNALS & STATE
  ✅  Simple Signal     →  Booleanos / Flags
  📡  Writable Signal   →  Estado general
  🛡️  Read-only Signal  →  asReadonly()
  💻  Computed          →  Estado derivado
  🚀  Effect            →  Efectos secundarios

COMPONENT I/O
  ⤵️  Input             →  Data Down
  ⤴️  Output            →  Event Up
  ↔️  Model             →  Two-way binding

ASYNC / RXJS
  👁️  Observable        →  Streams puros

INFRASTRUCTURE
  💉  Inject            →  Dependencias
  🔘  Const             →  Inmutables
  📝  Forms             →  FormGroup
  🧭  Router            →  Navegación

STRUCTURE
  🧩  Interface         →  Contratos
  🔢  Enum              →  Diccionarios
  🏷️  DOM Ref           →  viewChild / HTML refs
```

---

## ✅ Ejemplo completo en contexto

```ts
import { Component, computed, effect, inject, input, output, signal } from '@angular/core';
import { Router } from '@angular/router';

/* 🧩 */ interface Product {
  id: number;
  name: string;
  price: number;
}

/* 🔢 */ enum CartStatus {
  Empty   = 'EMPTY',
  HasItems = 'HAS_ITEMS',
}

@Component({ selector: 'app-cart', ... })
export class CartComponent {

  // — Injecciones —
  /* 💉 */ private readonly router = inject(Router);

  // — Inputs / Outputs —
  /* ⤵️ */ readonly products  = input.required<Product[]>();
  /* ⤴️ */ readonly purchased = output<Product[]>();

  // — Estado interno —
  /* ✅ */ readonly isOpen    = signal(false);
  /* 📡 */ readonly selected  = signal<Product[]>([]);

  // — Estado derivado —
  /* 💻 */ readonly total     = computed(() =>
    this.selected().reduce((sum, p) => sum + p.price, 0)
  );
  /* 💻 */ readonly status    = computed(() =>
    this.selected().length > 0 ? CartStatus.HasItems : CartStatus.Empty
  );

  // — Efectos —
  /* 🚀 */ readonly analytics = effect(() => {
    console.log('Cart updated:', this.total());
  });
}
```

---

*Convención L10 · Angular · Versión 1.0*  
*Actualiza este documento al evolucionar el sistema de iconografía del equipo.*
