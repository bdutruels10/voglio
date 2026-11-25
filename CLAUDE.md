# Voglio Gelateria: contexto del proyecto

Este archivo guarda lo decidido en la conversación con el usuario, para retomar el proyecto en una sesión nueva. Responder siempre en **español**.

## Qué es
- **El usuario:** arma esta plataforma para venderla a Voglio. Voglio es el emprendimiento de helados de la novia de un amigo del usuario.
- **Objetivo:** automatizar los pedidos, que hoy llegan por Instagram y WhatsApp; organizar el reparto; tener una lista de difusión por WhatsApp; y hacer crecer la marca.
- **Estado:** prototipo navegable en un solo archivo, `index.html`, con datos en memoria.
- **Versión publicada:** artefacto de Claude https://claude.ai/artifact/SziDqEWnoFwX3auAB77HFW.
- **Repositorio:** https://github.com/bdutruels10/voglio.

## Datos reales de Voglio
- **Fundadoras:** Caterina y Liliana, "Cate y Lili". El panel las saluda: "Hola, Cate y Lili".
- **Instagram:** @voglio.ec ("Voglio Gelateria", bio "Helado y punto").
- **WhatsApp Business:** +593 96 317 0910. En el catálogo, el martes aparece como "Cerrado".
- **Eslogan:** **"Helado y punto."** Frases del manual: "Passione e tradizione", "Hecho x amantes del gelato", "Más [sabor] x favor".
- **Zona:** Guayaquil y Samborondón.
- **Planta de producción:** Entre Ríos, Samborondón. **NO mostrarla al cliente.** Solo se usa internamente como punto de salida de las rutas (en el panel y en la app del repartidor).
- **Puntos de venta en percha** (solo para comprar; los pedidos de la web son **solo delivery**, sin retiro):
  - Del Portal: La Joya, Ciudad Celeste, La Piazza Samborondón, Moderna Plaza y Vía a la Costa.
  - Machala: Plaza Gourmet (solo en tienda, sin reparto).
- **Del Portal** es el distribuidor principal.
- **7 sabores con registro sanitario.** Tarrina de ½ litro (350 g); precios del catálogo de WhatsApp:
  - Pistacho $9.99
  - Chocolate $7.99
  - Avellana $7.99
  - Dulce de leche $6.99
  - Vainilla $5.99
  - Chicle $4.99
  - Menta con chocochips: precio **por confirmar** (en la página puse $7.99).
- **Vasitos:** se supone que vienen en todos los sabores (confirmar).
  - Vainilla: $2.50 (confirmado).
  - El resto: $3.00 marcado "por confirmar".
- **1 litro:** también lo venden, pero falta el precio. Por ahora la página solo ofrece ½ L y vasito.
- **Registro sanitario:** cuesta unos $1000 por producto. Por eso el "Sabor del mes" usa **combinaciones de sabores ya registrados** (packs), no sabores nuevos. Hay que confirmar con ARCSA si un pack necesita registro aparte.
- **Máquinas:** tienen máquinas de unos $20.000. Por eso el panel muestra el uso de capacidad.

## Marca (del manual, PDF que el usuario compartió y que NO está en el repositorio)
- **Colores principales:** crema `#F7E2D7`, celeste `#AABCC4`, lavanda `#B8B4D2`, negro `#151515`.
- **Colores de apoyo:** pistacho `#D1D7B2`, chocolate `#85513B`, azul `#3580AF`.
- **Tipografías:** Ultra (títulos), Raleway (textos), Reenie Beanie (frases escritas a mano). Candice no está en Google Fonts.
- **Logo:** letra tipo Cooper; se aproxima con Fraunces (SOFT 100). Falta el archivo real del logo.
- **Recursos gráficos:** monograma "V" y patrones de "V".
- **Envases reales:** tarrina blanca, tapa del color del sabor, etiqueta con el nombre en sílabas ("PIS-TA-CHO"). Vasito pequeño celeste con "Voglio" en crema y tapa del color del sabor.

## Qué tiene `index.html`
Tres vistas que comparten los mismos datos: **Cliente** (`#pedir`), **Repartidor** (`#repartidor`) y **Panel** (`#panel`).
- **Cliente:** vista simplificada a pedido del usuario: poco texto y sin pestañas. Arriba solo el logo y "Tu pedido"; "Mi pedido" aparece después de hacer un pedido. Eventos y "Para mi negocio" son tarjetas pequeñas debajo de los sabores. Texto del inicio: "hechos por Cate y Lili. Pide aquí y llegamos a la puerta de tu casa". Las dos son dueñas; en la web siempre van juntas.
  - Catálogo con foto de cada sabor y la tarrina o vasito ilustrado (SVG), con selector "½ litro | Vasito".
  - Modo "Para mi negocio": precio mayorista que se cotiza por WhatsApp; mínimo 10 tarrinas.
  - Checkout solo delivery: día, horario, pago y "¿Dónde te lo llevamos?": ubicación actual o pin en un mapa (Leaflet + OpenStreetMap, dentro de la página); si no, "¿En qué zona vives?". Las zonas son donde vive el cliente, no puntos de despacho.
  - "Para un evento" y "Para mi negocio" son botones en el inicio (sin emojis, sin botón "Pedir ahora"), para no bajar en el celular.
  - Panel > Eventos: contadores y tarjetas por estado (Nueva, Cotización enviada, Confirmado); "Enviar cotización" abre WhatsApp con el mensaje ya escrito.
  - **Eventos:** calculadora de tarrinas según invitados.
  - **Combo para compartir** (antes "Sabor del mes"): dos sabores más baratos juntos. No se dice "promoción": se muestra el precio normal tachado y "Ahorras $X". Precio de ejemplo $13.99 (por confirmar). Tiene votación.
  - **Mi pedido:** solo el estado (Recibido, En preparación, En camino, Entregado) más calificación con estrellas y opinión. **Sin mapa ni ubicación del repartidor**; el usuario lo pidió así.
- **Repartidor:** ruta optimizada (vecino más cercano + 2-opt), próxima parada, "Entregado" con método de pago y "No estaba" (pasa el pedido a mañana).
- **Panel:**
  - Pedidos (tablero por estado).
  - Reparto en vivo (mapa ilustrativo, lo que va pasando, efectivo cobrado, gasolina y ahorro).
  - Números (gráfico semanal, sabores, uso de máquinas, ganancia por tarrina).
  - Clientes y promos (opiniones, segmentos).
  - Combo (editor con foto del helado que se sube y aviso de cuánto ahorra el cliente) y Eventos.
  - Urgentes: Voglio marca un pedido como "urgente" y va primero en la ruta.
  - Ganancia por tarrina: costo distinto por sabor (valores de ejemplo; pedir los reales).
  - Gasolina: Extra/Ecopaís, Súper o Diésel con el precio oficial (objeto `FUEL` en `index.html`). El usuario quiere que se revisen cada semana.
- **Administrador** (`#admin`): solo para el usuario, no para Voglio. Tiene lo automático (WhatsApp, hora límite, martes), el plan de mantenimiento mensual ($50 de ejemplo) y los precios de combustible. El usuario quiere cobrarles mantenimiento mensual por esto.
- **Repartidor:** también puede tocar "Ir primero" para cambiar el orden, y elige el combustible de su moto.
- **Fotos de sabores:** de Pexels, licencia libre (IDs en el README). `img/hero.jpg` es la foto real de las tarrinas de Voglio.

## Pendientes
1. **GitHub Pages:** ya funciona en https://bdutruels10.github.io/voglio/ (desde `main` / root, con `.nojekyll`).
2. **Confirmar con Voglio:**
   - Precios de 1 L, vasitos, menta y mayorista.
   - Si hay vasitos de todos los sabores.
   - El martes cerrado.
   - Dirección exacta de la planta (para la ruta).
   - Costo por tarrina y capacidad de las máquinas.
3. **Pedirles:** logo en archivo y fotos propias de cada sabor, para reemplazar las de Pexels.
4. **Versión real:** base de datos y cuentas, WhatsApp Business API, Google Maps (ubicación al pedir y rutas reales), pagos (Payphone o Kushki), dominio (voglio.ec).

## Notas técnicas
- **Entorno:** la red permite unsplash.com, images.unsplash.com e images.pexels.com.
- **Artefacto:** para republicarlo se usa el archivo `index.html` de este repositorio.
- **Repositorio:** el usuario autorizó (25 nov 2026) hacer commit y push a `main` de cada cambio sin preguntar. Después de cada push, GitHub Pages se publica solo en uno o dos minutos.
