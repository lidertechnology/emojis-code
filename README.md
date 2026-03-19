💎 Protocolo de Formato y Arquitectura Visual L10
1. Bloque de Importaciones (Imports)
Agrupación: Separar por bloques: 1. Angular, 2. Material Modules, 3. Recursos propios (Interfaces, Servicios, Constantes).

Alineación de Columna: Los nombres de los elementos importados deben estar alineados verticalmente, al igual que las rutas from.

Imports de Componente: Dentro del decorador @Component, la propiedad imports: [ ... ] debe escribirse en una sola línea para mantener la brevedad visual del decorador.

2. Decorador @Component
Alineación: Alinear los dos puntos : de todas las propiedades (selector, templateUrl, etc.).

Performance: Usar changeDetection: ChangeDetectionStrategy.OnPush siempre que sea posible.

Standalone: standalone: true es el estándar por defecto.

3. Matriz de Identidad Visual (Iconografía Declarativa)
Cada propiedad o bloque debe llevar su emoji identificador. Se aplica alineación de columna estricta para el signo =.


💎 Matriz de Identidad Visual L10 (Actualizada)

# 1. Infraestructura y Dependencias:
        /* 💉 */ Inyección: Uso exclusivo de inject() para servicios, tokens o datos.
        /* 🔒 */ Constantes: Reservado estrictamente para constantes inmutables o de solo lectura.
        /* 🚨 */ Navegación: IDs de ruta, ActivatedRoute, Router y estados de modo (isEditMode).

# 2. Reactividad Moderna (Signals).
   
        /* 💡 */ Signal: Estado mutable de entrada o señal básica (signal).
        /* 🖥️ */ Computed: Señales de valores derivados o calculados (computed).
        /* ✨ */ Effect: Efectos secundarios reactivos (effect).
        /* 🪃 */ Model: Comunicación bidireccional moderna (model).

# 3. Comunicación y DOM:
        /* ↘️ */ Input: Entrada de datos desde un componente padre (@Input).
        /* ↗️ */ Output: Salida de eventos hacia componentes superiores (@Output).
        /* 👀 */ ViewChild: Referencias a elementos del DOM o componentes hijos (@ViewChild).
        /* 🏷️ */ Elemento: Referencias directas a ElementRef o nodos nativos.

# 4. Arquitectura de Formularios:
        /* 📝 */ Formulario: Declaración y estructura de la variable formGroup.
        /* ✅ */ Validador: Reglas de validación dentro de los controles (Validators).

# 5. Flujos Asíncronos (RxJS):
        /* 👁️ */ Observable: Flujos de datos asíncronos (Observable, Subject).
        /* 📌 */ Suscripción: Anclas de Subscription que requieren limpieza manual.

# 6. Estructura de Métodos:
        /* 🚧 */ Constructor: Bloque inicial de construcción (zona de cimientos).
        /* 🅰️ */ Angular Nativo: Hooks de ciclo de vida (ngOnInit, ngOnDestroy, etc.).
        /* 🏛️ */ Método L10: Lógica de negocio, funciones privadas y procesos propios.

