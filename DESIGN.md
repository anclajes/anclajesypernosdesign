# DESIGN.md — Anclajes y Pernos SAC (sitio web, versión catálogo industrial)

Mundo visual: catálogo industrial de fabricante. El producto real, recortado y sin caja, es la imagen principal. Forma propia: esquinas achaflanadas como el canto de una tuerca, en paneles, tarjetas y botones.

Referencias que lo inspiran (ver Diseños/referencias-web): Bolt Base (azul de marca plano, mosaico de categorías, banda oscura), Würth y United Fasteners (buscador protagonista, franja de confianza), Ganter Norm (piezas recortadas como héroe), TR Fasteners, INA y Metacom (plano junto al cuadro de medidas, caja de cotización), Makers Bolt (forma propia repetida, amarillo de señal).

## Color
| Token | Valor | Uso |
|---|---|---|
| blanco | #FFFFFF | fondo |
| humo | #EEF0F3 | mesas de producto, tarjetas, paneles |
| humo-2 | #E2E6EB | hover de tarjetas |
| linea | #D3D8DF | separadores |
| gris | #556070 | texto secundario |
| navy | #0D1B3D | texto, franja superior, bandas oscuras |
| azul | #0B5BD3 | marca: botones primarios, enlaces, mosaico de Anclajes, llamada final |
| azul-2 | #0848A8 | hover |
| señal | #F5B800 | solo acción de cotizar y acentos de rótulo |

## Tipografía
Saira variable (Google Fonts). Títulos con ancho 110–112 y peso 700–720; cuerpo ancho 100, 17px. Números tabulares en todo el sitio.

## Componentes
- Chaflán `.ch` (clip-path de 8 puntos, --ch entre 8 y 26px según tamaño).
- Botones: azul (primario), señal (cotizar), borde navy (secundario), blanco sobre fondos oscuros.
- Mesa del héroe: piezas recortadas con sombra real, etiqueta técnica al pasar el cursor o enfocar; cada pieza abre su ficha.
- Mosaico de líneas: celda grande azul para Anclajes, resto en humo, filete superior azul (amarillo en la celda azul).
- Tarjeta de producto: marco humo achaflanado, recorte centrado, distintivo de stock, línea, nombre, normas.
- Ficha: galería foto/plano, datos clave con ícono y filete amarillo, caja "Cotiza este producto" (medida, acabado, cantidad a WhatsApp), pestañas, plano fijo junto al cuadro de medidas.
- Catálogo: filtros por línea, sistema de medida, material, acabado y norma, con conteos.

## Movimiento
Una sola secuencia de carga: las piezas de la mesa caen y se asientan. El resto es respuesta del usuario (hover de piezas y tarjetas, cambio foto/plano, transición de vista). Videos con botón de pausa; con movimiento reducido no se reproducen solos.

## Procedencia de imágenes
- Recortes (img/recorte): generados de las fotos de producto del cliente quitando el fondo blanco (relleno desde el borde; contorno convexo en tuercas y arandelas).
- Fotos, planos y videos: material del cliente en Diseños (ver versión anterior).

## Versión 6 (actual, index.html)
- La versión 5 quedó guardada como version-5-catalogo.html.
- Encabezado de una sola fila (72 px): logo, Productos (mega menú con foto por línea y lista de productos), Fabricación a plano, Guía técnica, Contacto; a la derecha Buscar (abre un buscador superpuesto, también con la tecla /) y Cotizar.
- En inicio el encabezado es transparente sobre el video y usa img/logo-blanco.webp; al bajar o en otras páginas pasa a blanco.
- Portada a pantalla completa con video 5 (torre en la montaña), titular grande en blanco y barra de las 5 líneas con sus piezas recortadas montada sobre el borde inferior.
- Secciones separadas por color: blanco (De línea) → azul con retícula (piezas interactivas sobre la mesa) → humo (líneas) → navy con video 6 (certificado) → blanco (fabricación) → humo (marcas) → amarillo señal (cotizar) → pie navy.
- Páginas internas (catálogo, guía, contacto) con cabecera navy con retícula y una pieza recortada.
