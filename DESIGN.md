# DESIGN.md — Anclajes y Pernos SAC (sitio web, versión 8 "oscura")

Cliente: Anclajes y Pernos SAC, Comas, Lima. Fabricante e importador de pernería (pernos, tuercas, arandelas, varillas roscadas) y anclajes fabricados a plano, para construcción, minería, energía y telecomunicaciones.

Objetivo del sitio: que el cliente de obra encuentre la pieza, confirme la norma y la medida, y cotice por WhatsApp en pocos toques. El cliente suele llegar desde el celular.

Mundo visual: una sala oscura y sobria, como la vitrina de una marca de producto premium. Las piezas recortadas y las fotos de obra y taller se muestran como protagonistas sobre el negro. Hay pocos acentos de color: un solo azul de acción.

## Archivos
- `index.html` es la versión vigente (8), un solo archivo con CSS y JS en línea. Contiene todas las vistas (inicio, catálogo, ficha, fabricación, guía, contacto), que se alternan con `section.vista[data-vista]`.
- El CSS tiene dos capas: la base heredada de la versión 6 (tokens claros, `.t-*`, `.btn`, `.ch`) y, desde `:root{--negro…}`, la capa de la versión 8, que la sobrescribe con clases `.n-*`. Al editar, se cambia la capa 8 y no se toca la base, salvo para limpiarla.
- Las versiones anteriores (`version-*.html`) son solo de referencia. El historial real está en git.
- Imágenes:
  - `img/recorte`: piezas sin fondo.
  - `img/*-plano`: planos técnicos.
  - `img/foto`: fotos de ambiente optimizadas en webp.
  - `media`: videos 5 (torre) y 6 (certificado) con su póster.
  - `img/nuevas`: originales pesados. No se publican; están en `.gitignore`.

## Color (capa 8)
| Token | Valor | Uso |
|---|---|---|
| negro | #0C0D0F | fondo general, encabezado, pie |
| panel | #151719 | tarjetas y marcos de foto |
| panel-2 | #1C1F22 | relleno secundario |
| hilo | rgba(255,255,255,.10) | separadores y bordes |
| texto-g | #9BA1A9 | texto secundario sobre negro |
| claro | #F3F3F1 | tarjeta clara ("Por qué trabajar…") |
| acento | #1F78E0 | única acción: botones, enlaces, foco, llamada final |
| acento-2 | #1964BE | hover del acento |

Los tokens heredados (navy, azul, señal #F5B800, humo) siguen en uso en las vistas internas que aún no se migraron a la capa 8.

## Tipografía
Figtree variable (Google Fonts, 300–800).
- Títulos ligeros y grandes:
  - `.n-h1`: peso 350, hasta 118px, tracking −0.045em.
  - `.n-h2`: peso 380, hasta 72px.
- Cuerpo: 15–17px, con texto secundario en `texto-g`.
- Números tabulares en todo el sitio.

## Componentes
- Encabezado negro fijo: logo blanco, Productos (mega menú), Fabricación a plano, Guía técnica y Contacto. A la derecha, Buscar (también con la tecla /) y Cotizar. En móvil queda el logo con los botones Buscar y Menú.
- Barra inferior fija en móvil con Llamar (tel:+51940479303) y WhatsApp (wa.me con texto prellenado).
- Botones con radio de 3px: acento (primario), borde blanco translúcido (`.btn-osc`) y blanco (`.btn-bl`). El chaflán `.ch` está desactivado en la capa 8.
- Tarjetas de línea (`.n-carta`): marco panel de 3:4 con brillo radial, la pieza recortada con sombra, y debajo el nombre y el conteo de productos. Al pasar el cursor hay un borde acento y la pieza gira.
- Fotos (`.n-foto`) con radio de 4px y revelado tipo cortina azul al entrar en pantalla.
- Iconos en círculo azul translúcido (`.ic`).

## Secciones del inicio (en orden)
1. Héroe: titular partido ("Pernería con norma, / lista para despachar."), foto de unión empernada, subtítulo y botones Ver el catálogo y Pedir una cotización.
2. Lo que hacemos (`.n-trabajo`): foto del taller y beneficios con ícono.
3. Líneas (`.n-lineas`): "Para cada unión de tu obra", con 5 tarjetas de línea.
4. Banda con foto (`.n-banda`): "De la cimentación a la cima de la torre" y los sectores.
5. Razones (`.n-razones`): tarjeta clara con foto del almacén y 3 razones.
6. Proceso (`.n-proceso`): fabricación paso a paso con fotos.
7. Explora (`.n-explora`): foto alta y video.
8. Calidades (`.n-cal`): marcas de grado (F1554 36/55/105, etc.) sobre panel.
9. Llamada final azul (`.n-llam`) y pie negro.

## Movimiento
- Al cargar: el titular entra desde los lados, la pieza sube y se enciende el brillo.
- Al bajar: revelado `data-rev` con desplazamiento, y fotos con cortina `data-cortina`.
- Todo va dentro de `prefers-reduced-motion: no-preference`. Los videos tienen botón de pausa.

## Procedencia de imágenes
- Recortes, planos y videos: material del cliente.
- Fotos de `img/foto`: generadas con IA (Gemini) a partir de indicaciones, y optimizadas a webp. **Pendiente: reemplazarlas por fotos reales de la planta y de obras del cliente.** Una empresa que vende con certificado no debe mostrar como propio un taller o una planta que no existen.

## Pendientes conocidos
- En móvil, la barra fija Llamar/WhatsApp tapa el final del texto del héroe.
- Hay mucho espacio vacío antes de "Para cada unión de tu obra".
- Faltan las etiquetas Open Graph (vista previa al compartir por WhatsApp) y los datos estructurados LocalBusiness.
- Hay 19 imágenes con `alt=""`. Se debe revisar cuáles son decorativas y cuáles necesitan descripción.
- Las vistas internas (catálogo, ficha, guía) mezclan las dos capas de estilo.
