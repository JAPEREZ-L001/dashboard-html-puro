# Dashboard HTML Puro

Demo del ejercicio: comunicar datos de un **formulario** a un **dashboard** con estas restricciones:

- Solo **HTML** (sin JavaScript)
- Solo método **GET**
- Sin **backend**

## Estructura

```
dashboard-html-puro/
├── index.html      → formulario + iframe embebido
├── dashboard.html  → página destino que recibe los parámetros GET
└── README.md
```

## Cómo funciona

El formulario usa dos atributos clave:

```html
<form action="dashboard.html" method="GET" target="dashboard-frame">
```

- `method="GET"` → codifica los datos como parámetros en la URL (`?nombre=ana&rol=estudiante`)
- `target="dashboard-frame"` → carga la respuesta dentro del `<iframe name="dashboard-frame">` en vez de recargar toda la página

## Limitación honesta

**Sin JavaScript ni backend, el HTML puro NO puede leer los parámetros de la URL para renderizarlos como contenido visual dinámico.**

Lo único que sucede es:
1. Los datos viajan en la URL del iframe ✅
2. La URL con los parámetros es visible ✅
3. Pero el HTML del `dashboard.html` no puede extraer esos valores y mostrarlos como texto ❌

## Workarounds posibles (sin JS ni backend)

1. **Páginas estáticas predefinidas**: si las opciones del formulario son finitas, se pueden generar múltiples archivos HTML (`dashboard-ana.html`, `dashboard-carlos.html`, etc.) y usar `<a href>` en vez de `<input>`.
2. **Fragmentos con `:target` CSS**: usar `#seccion` y el pseudo-selector `:target` en CSS para mostrar/ocultar bloques según el ancla.
3. **Aceptar que la URL misma es el mensaje**: el usuario ve los parámetros en la barra del navegador.

## Conclusión

El ejercicio, tal cual está planteado (comunicación dinámica de datos entre dos páginas HTML sin JS ni backend), **teóricamente no es resoluble** en el sentido tradicional. Lo mejor que se puede hacer es simular la interacción con enrutamiento estático o exponer la URL como canal de datos.
