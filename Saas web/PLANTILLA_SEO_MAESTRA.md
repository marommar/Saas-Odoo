# 🥇 Guía y Plantilla Maestra de Optimización SEO y WPO

Esta guía es un manual de referencia paso a paso para implementar una estrategia SEO técnica, On-Page, de rendimiento y accesibilidad perfecta (puntuación 100/100 en Google PageSpeed y Seobility) en cualquier proyecto web futuro.

---

## 1. El `<head>` Perfecto (SEO Técnico)

El `<head>` del HTML es lo primero que leen los bots de Google y las redes sociales. 

### ¿Por qué es importante?
Define cómo te ves en Google (título y descripción) y cómo te ves al compartir el enlace por WhatsApp/Twitter (tarjetas grandes con imagen). También evita penalizaciones por contenido duplicado.

### 📋 Plantilla para Copiar y Pegar:

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- 1. Etiquetas Básicas -->
    <title>Nombre de tu App | Palabra Clave Principal</title>
    <meta name="description" content="Descripción persuasiva de 150-160 caracteres. Incluye la propuesta de valor y palabras clave relevantes para incentivar el clic en Google.">
    <meta name="keywords" content="palabra1, palabra2, palabra3, SaaS, app, online"> <!-- Usa términos de un análisis TF-IDF -->

    <!-- 2. Open Graph (Para Facebook, LinkedIn, WhatsApp) -->
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://tudominio.com/">
    <meta property="og:title" content="Nombre de tu App | Propuesta de Valor">
    <meta property="og:description" content="La misma descripción de arriba o una variante más orientada a redes.">
    <meta property="og:image" content="https://tudominio.com/og-image.png"> <!-- Imagen 1200x630px -->
    <meta property="og:image:alt" content="Descripción de la imagen para accesibilidad">

    <!-- 3. Twitter Cards -->
    <meta property="twitter:card" content="summary_large_image">
    <meta property="twitter:url" content="https://tudominio.com/">
    <meta property="twitter:title" content="Nombre de tu App | Propuesta de Valor">
    <meta property="twitter:description" content="Descripción persuasiva.">
    <meta property="twitter:image" content="https://tudominio.com/og-image.png">

    <!-- 4. Indexación e Idioma -->
    <link rel="canonical" href="https://tudominio.com/"> <!-- Evita contenido duplicado -->
    <link rel="alternate" hreflang="es" href="https://tudominio.com/"> <!-- Idioma principal -->
    <link rel="alternate" hreflang="x-default" href="https://tudominio.com/"> <!-- Por defecto -->

    <!-- 5. Favicon -->
    <link rel="icon" href="/favicon.svg" type="image/svg+xml">

    <!-- 6. Precarga de Recursos (WPO) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=TuFuente:wght@400;600&display=swap" rel="stylesheet">
    
    <!-- CSS (SIN @import dentro del CSS para evitar bloqueo de renderizado) -->
    <link rel="stylesheet" href="style.css">
</head>
```

---

## 2. Archivos Técnicos de Rastreo

Todo proyecto que subas a producción debe tener obligatoriamente dos archivos en la carpeta raíz (junto al `index.html`):

### A. `robots.txt`
Indica a los bots (Googlebot, Bingbot) qué partes de tu web pueden leer y cuáles no.

**Plantilla base:**
```text
User-agent: *
Allow: /

Sitemap: https://tudominio.com/sitemap.xml
```

### B. `sitemap.xml`
Es un mapa que le dice a Google qué páginas/secciones existen y cuándo se actualizaron.

**Plantilla base (Para Landing Page con secciones):**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <!-- Página Principal -->
  <url>
    <loc>https://tudominio.com/</loc>
    <lastmod>2026-05-07</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
  <!-- Ejemplo: Sección interna o ancla -->
  <url>
    <loc>https://tudominio.com/#registro</loc>
    <priority>0.8</priority>
  </url>
</urlset>
```

---

## 3. SEO On-Page y Estructura Semántica HTML5

Google no tiene ojos, lee etiquetas. Si usas puros `<div>`, Google no sabe qué es importante.

### Reglas de Oro:
1. **Jerarquía `<h1> - <h6>`:** 
   * SOLO puede haber un `<h1>` por página. Debe contener la palabra clave más fuerte.
   * Los `<h2>` son los subtítulos principales (secciones).
   * No saltes de `<h2>` a `<h4>`. Ve en orden.
2. **Etiquetas Semánticas:**
   * Usa `<header>` para el menú.
   * Usa `<main>` para envolver TODO el contenido principal.
   * Usa `<section>` para cada bloque de la web (Beneficios, FAQ, Precios).
   * Usa `<footer>` para el pie de página.
3. **Imágenes SEO:**
   * Toda imagen `<img src="...">` DEBE tener el atributo `alt="Descripción exacta de lo que se ve"`.

---

## 4. Algoritmo TF-IDF (El Secreto de los Textos)

Google posiciona los textos analizando la densidad y relevancia de las palabras. **TF-IDF** (Term Frequency – Inverse Document Frequency) calcula qué palabras usa tu competencia y tú no.

*   **Cómo aplicarlo:** Utiliza herramientas como *Seobility* o *Ahrefs* para analizar a la competencia.
*   **Implementación:** Si haces una web de "Software para Restaurantes", el TF-IDF te dirá que debes mencionar: *TPV, comandas, mesas, inventario, hostelería, nube*. Si no las mencionas, Google considerará que tu web es pobre en contexto.
*   **Regla:** Jamás crees "Thin Content" (páginas con menos de 300 palabras). Añade siempre secciones de Beneficios, "Cómo Funciona" y FAQs para nutrir la web de palabras clave.

---

## 5. Datos Estructurados (Schema.org / JSON-LD)

Es código oculto en el `<head>` o al final del `<body>` que alimenta directamente el cerebro lógico de Google. Permite aparecer en los "Resultados Enriquecidos" (Rich Snippets), como las cajitas de preguntas frecuentes o las estrellitas de reviews.

**Ejemplo para una página de Software SaaS:**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "name": "Nombre de tu App",
  "applicationCategory": "BusinessApplication",
  "operatingSystem": "Web",
  "description": "Tu descripción SEO.",
  "offers": {
    "@type": "Offer",
    "price": "0",
    "priceCurrency": "EUR"
  }
}
</script>
```

---

## 6. Rendimiento y WPO (Core Web Vitals)

Google mide la experiencia del usuario (tiempos de carga). Si la web carga lento, no rankeas.

*   **Evitar CDN Bloqueantes:** Frameworks como Tailwind por CDN (`<script src="https://cdn.tailwindcss.com"></script>`) bloquean el renderizado porque el navegador debe compilar el CSS en tiempo real. **Solución:** Usar Tailwind mediante compilación en build (PostCSS) o usar Vanilla CSS puro.
*   **No usar `@import` en CSS:** Si pones `@import url('googlefonts')` dentro de tu `style.css`, obligas al navegador a descargar el CSS y, al terminar, darse cuenta de que necesita descargar las fuentes. Eso genera retrasos en el LCP. Pon los `<link>` de las fuentes directamente en el HTML.
*   **Fuentes (Swap):** Siempre añade `&display=swap` al final de la URL de Google Fonts para que el navegador muestre texto con una fuente del sistema inmediatamente mientras descarga la oficial.

---

## 7. Accesibilidad (WCAG)

Si tu web no la puede leer una persona con discapacidad visual, Google te penaliza (bajando el score en Lighthouse/PageSpeed).

1.  **Ratio de Contraste (WCAG AA/AAA):** El texto debe destacar MUCHO sobre el fondo.
    *   Fondo Oscuro -> Texto Secundario debe ser un Gris muy claro (`#cbd5e1` o `#e2e8f0`).
    *   Botón Primario -> El color de fondo y el texto blanco deben contrastar bien. Si el botón es azul claro, el texto blanco no se lee; usa un azul oscuro.
2.  **Formularios para Lectores de Pantalla:**
    Todo `<input id="email">` debe ir acompañado de un `<label for="email">`. Ese atributo `for` conecta el texto con la caja de entrada para que las tecnologías de asistencia sepan qué debe escribir el usuario ahí.

---
*Fin de la guía. Guárdala como referencia para aplicarla como check-list inicial en todos los desarrollos web futuros.*
