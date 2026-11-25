# Voglio Gelateria · Pedidos y gestión

Prototipo navegable de la plataforma de pedidos de **Voglio** (Guayaquil y Samborondón, Ecuador).
*Helado y punto.*

Es una sola página (`index.html`) con tres vistas que comparten los mismos datos. Lo que cambia en una se ve en las otras:

| Vista | Para quién | Qué hace |
|---|---|---|
| **Cliente** (`#pedir`) | Quien compra | Catálogo de los 7 sabores en ½ litro y vasito, pedido a domicilio, cotización de eventos (`#eventos`), sabor del mes y votación (`#mes`), seguimiento del pedido con calificación y opinión (`#seguimiento`). |
| **Repartidor** (`#repartidor`) | Quien reparte | Ruta del día ordenada para gastar menos gasolina, próxima parada, cobro (efectivo o transferencia), "Entregado" y "No estaba". |
| **Panel de Voglio** (`#panel`) | Las dueñas | Tablero de pedidos por estado, reparto en vivo con mapa, números (ventas, sabores, uso de máquinas, ganancia por tarrina), clientes y promociones, automatizaciones de WhatsApp, editor del sabor del mes y cotizaciones de eventos. |

## Cómo verlo

Abre `index.html` en el navegador. Si las fotos no cargan al abrirlo como archivo, sírvelo con un servidor local:

```bash
python3 -m http.server 8000
```

Después entra a <http://localhost:8000>.

## Recorrido de prueba

1. **Cliente:** agrega sabores, abre "Tu pedido" y confirma.
2. **Panel → Pedidos:** toca **Confirmar** en el pedido nuevo.
3. **Repartidor:** toca **Salir a repartir** y luego **Entregado** en cada parada.
4. **Cliente → Mi pedido:** mira el estado y deja una calificación.
5. **Panel → Reparto en vivo / Automático:** revisa el mapa, lo cobrado y los mensajes enviados.

## Estado actual: es un prototipo

- **Datos:** todo vive en memoria. Al recargar la página vuelven los datos de ejemplo.
- **WhatsApp:** los mensajes automáticos se muestran en el panel pero no se envían. Para enviarlos hace falta conectar WhatsApp Business.
- **Mapa:** es un dibujo con ubicaciones aproximadas. La versión real usaría Google Maps con la dirección exacta del cliente.
- **Datos de ejemplo por confirmar con Voglio:**
  - Precios de los vasitos, salvo el de vainilla.
  - Precio de Menta con chocochips.
  - Precio mayorista.
  - Costo por tarrina y capacidad de las máquinas.
  - Clientes, ventas y repartidor.

Los precios de ½ litro vienen del catálogo de WhatsApp de Voglio.

## Próximos pasos sugeridos

1. Base de datos y cuentas: guardar pedidos y clientes, y dar acceso al panel y al repartidor.
2. WhatsApp Business: confirmaciones, avisos de "va en camino" y promociones.
3. Google Maps: ubicación al pedir, rutas reales y ubicación del repartidor.
4. Pagos en línea: Payphone o Kushki.
5. Dominio propio, por ejemplo voglio.ec.

## Marca

Colores, tipografías y frases tomados del manual de marca de Voglio:
- **Colores:** crema `#F7E2D7`, celeste `#AABCC4`, lavanda `#B8B4D2` y negro `#151515`, con azul, pistacho y chocolate de apoyo.
- **Tipografías:** Ultra, Raleway y Reenie Beanie, desde Google Fonts.
- **Logo:** se aproxima con Fraunces mientras no tengamos el archivo del logo.

## Fotos

- `img/hero.jpg`: foto de las tarrinas de Voglio.
- `img/pistacho.jpg`, `chocolate.jpg`, `dulcedeleche.jpg`, `avellana.jpg`, `menta.jpg`, `vainilla.jpg`, `chicle.jpg`: fotos de [Pexels](https://www.pexels.com/license/), libres de uso comercial. IDs: 3770058, 1346341, 14132776, 8589559, 5713992, 7491892, 8093197.

Lo ideal es reemplazarlas por fotos propias de cada sabor.
