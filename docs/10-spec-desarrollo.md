# Spec de desarrollo — Ruliette

> Guía: [Spec de desarrollo](../evaluacion/guias/fase-2-specs/07-spec-de-desarrollo.md)

## Insumos y prompt para el asistente

```text
Lee DESIGN.md, docs/09-spec-diseno.md y docs/10-spec-desarrollo.md.
En la carpeta stitch/ está el código exportado de Stitch de cada pantalla.
Construye el sitio siguiendo exactamente docs/10-spec-desarrollo.md:
solo HTML y CSS, la estructura de archivos y la navegación definidas,
las variables de :root con los valores de DESIGN.md y la estructura
semántica de cada página. Usa el código de Stitch solo como referencia
visual. Al terminar, revisa cada criterio de aceptación y dime cuáles
se cumplen y cuáles no.
```

## 1. Estructura de archivos

mi-emprendimiento/
    index.html              # Landing page principal
    tienda.html             # Catálogo general de impresiones y cuadros
    producto.html           # Detalle y ficha técnica de obra de autor
    carrito.html            # Resumen de compra y cálculo de despacho
    blog.html               # Historias de expedición y guías de decoración
    articulo.html           # Artículo individual del blog
    css/
        styles.css          # Hoja de estilos global unificada
    img/                    # Fotografías e íconos optimizados
        hero-portada.jpg
        obras/
        blog/
    DESIGN.md               # Sistema de diseño para Stitch / Código
    docs/                   # Documentación académica de la Fase 2

## 2. Páginas y navegación

| Desde | Elemento | Lleva a |
|---|---|---|
|Todas las páginas|Logo "Ruliette" en Navbar|index.html (Landing)|
|Todas las páginas|Enlace "Inicio" en Navbar|index.html (Landing)|
|Todas las páginas|Enlace "Tienda" en Navbar|tienda.html|
|Todas las páginas|Enlace "Historias" en Navbar|blog.html|
|Todas las páginas|Enlace "Sobre mí" en Navbar|blog.html|
|Todas las páginas|Enlace "Contacto" en Navbar|blog.html|
|Todas las páginas|Ícono Bolsa de compras|carrito.html|
|index.html|Botón "Explorar Colección"|tienda.html|
|tienda.html|Tarjeta de producto|producto.html|
|producto.html|Botón "Agregar a la Bolsa"|carrito.html|
|carrito.html|Botón "Proceder al Pago seguro"|checkout.html|
|blog.html|Tarjeta de artículo|articulo.html|


## 3. Estructura semántica

Cada archivo HTML del sitio debe respetar la siguiente jerarquía semántica estándar:

- <header>: Contiene el cintillo promocional y la barra de navegación <nav> con la lista de enlaces e íconos de acción.
- <main>: Envuelve todo el contenido único y principal de cada vista.
  - <section>: Define las secciones principales (e.g., Hero, Catálogo, Artículos destacados).
  - <article>: Encapsula elementos independientes y reutilizables como tarjetas de productos (.card-product) o entradas del blog (.card-article).
  - <aside>: Para paneles laterales de filtros en la tienda o índices de contenido en artículos.
- <footer>: Contiene enlaces institucionales, redes sociales, aviso de copyright y enlaces legales.
## 4. Organización del CSS

```css
:root {
  /* Paleta de Colores (Extraídos de DESIGN.md) */
  --verde-bosque: #2C3E35;
  --tierra-organica: #8C6D53;
  --mostaza-silvestre: #D99B26;
  --crema-arena: #F9F8F3;
  --carbon-profundo: #1F2421;
  --verde-exito: #4A7C59;
  --terracota-error: #B85B48;
  --blanco: #FFFFFF;

  /* Tipografías */
  --font-titulos: 'Playfair Display', serif;
  --font-textos: 'Plus Jakarta Sans', sans-serif;

  /* Tamaños Tipográficos Desktop */
  --h1-desktop: 48px;
  --h2-desktop: 36px;
  --h3-desktop: 24px;
  --p-desktop: 16px;

  /* Tamaños Tipográficos Mobile */
  --h1-mobile: 32px;
  --h2-mobile: 26px;
  --h3-mobile: 20px;
  --p-mobile: 15px;

  /* Pesos */
  --weight-regular: 400;
  --weight-medium: 500;
  --weight-semibold: 600;
  --weight-bold: 700;

  /* Layout y Espaciados */
  --max-width: 1200px;
  --border-radius: 8px;
}

## 5. Criterios de aceptación

**Navegación**
- [ ] El menú superior (Navbar) está presente en las 6 páginas del sitio y mantiene coherencia de enlaces.
- [ ] Todos los enlaces de navegación conducen a la página de destino correspondiente según la tabla de navegación.
- [ ] Es posible realizar el flujo completo desde la portada hasta el carrito de compras.

**Funcionalidades**
- [ ] La tienda presenta filtros de búsqueda por categorías de paisaje y formato.
- [ ] La ficha de producto incluye opciones para seleccionar tamaño de cuadro y tipo de marco.
- [ ] El carrito refleja el listado de ítems seleccionados y calcula el subtotal de compra.

**Diseño**
- [ ] El sitio aplica rigurosamente la paleta de colores definida en DESIGN.md mediante variables en :root.
- [ ] Se respeta la jerarquía tipográfica con Playfair Display para títulos y Plus Jakarta Sans para párrafos.
- [ ] El diseño refleja la estética serena, editorial y sustentable de la marca Ruliette.

**Responsive**
- [ ] Todas las páginas se adaptan correctamente a pantallas móviles (375px) sin generar desbordamiento horizontal.
- [ ] En pantallas pequeñas, el menú de navegación se colapsa y las cuadrículas se organizan a una sola columna.

**Accesibilidad y publicación**
- [ ] Los contrastes entre texto y fondo cumplen con las relaciones mínimas de la norma WCAG (mínimo 4.5:1).
- [ ] Todas las imágenes cuentan con el atributo alt descriptivo.
- [ ] El código está limpio, libre de scripts innecesarios y estructurado usando etiquetas HTML5 semánticas.
