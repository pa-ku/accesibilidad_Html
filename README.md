# accesibilidad_Html

### Omite el valor de los atributos booleanos

Es más fácil de escribir, ¿no es así?

Mal:

```
<audio autoplay="autoplay" src="/audio/theme.mp3">
```

Bien:

```
<audio autoplay src="/audio/theme.mp3">
```

### Usa semánticas ARIA implícitas

Si un elemento tiene un ARIA `role` implícitamente en un documento HTML, no lo especifiques.

Mal:

```
<nav role="navigation">
  ...
</nav>

<hr role="separator">
```

Bien:

```
<nav>
  ...
</nav>

<hr>
```

## El elemento raíz

### Añade el atributo `lang`

El atributo `lang` ayudará a traducir un documento HTML.

Mal:

```
<html>
```

Bien:

```
<html lang="en-US">
```

### Evita `data-*` tanto como sea posible

Los navegadores pueden manejar adecuadamente un atributo apropiado.

Mal:

```
<span data-language="french">chemises</span>
...
<strong data-type="warning">Do not wash!</strong>
```

Bien:

```
<span title="French"><span lang="fr">chemises</span></span>
...
<strong class="warning">Do not wash!</strong>
```

## Metadatos del documento

### Añade un elemento `title`

Un valor para el elemento `title` puede ser usado por varias aplicaciones, no solamente el navegador.

Mal:

```
<head>
  <meta charset="UTF-8">
</head>
```

Bien:

```
`<head>   <meta charset="UTF-8">   <title>HTML Best Practices</title> </head>`
```

### Especifica el MIME type de recursos menores vinculados

Es una pista acerca de cómo la aplicación maneja el recurso.

Mal:

```
<link href="/pdf" rel="alternate">
<link href="/feed" rel="alternate">
<link href="/css/screen.css" rel="stylesheet">
```

Bien:

```
<link href="/pdf" rel="alternate" type="application/pdf">
<link href="/feed" rel="alternate" type="application/rss+xml">
<link href="/css/screen.css" rel="stylesheet">
```

### No uses un link para `favicon.ico`

Casi todos los navegadores obtienen `/favicon.ico` de forma automática y asíncrona.

Mal:

```
<link href="/favicon.ico" rel="icon" type="image/vnd.microsoft.icon">
```

Bien:

```
<!-- Pon `favicon.ico` en el directorio raíz. -->
```

### Añade un link para `apple-touch-icon`

Informa qué icono utilizan las plataformas iOS para representar el sitio.

Mal:

```
<!-- Oye Apple! Por favor descarga `/apple-touch-icon.png`! -->
```

Bien:

```
<link href="/apple-touch-icon.png" rel="apple-touch-icon">
```

### Añade el atributo `title` a las hojas de estilo alternativas

Un título comprensible para los humanos ayuda a las personas a elegir la hoja de estilo adecuada.

Mal:

```
<link href="/css/screen.css" rel="stylesheet">
<link href="/css/high-contrast.css" rel="alternate stylesheet">
```

Bien:

```
<link href="/css/screen.css" rel="stylesheet">
<link href="/css/high-contrast.css" rel="alternate stylesheet" title="High contrast">
```

### Para URLs, usa el elemento `link`

El valor del atributo `href` se puede resolver como una URL.

Mal:

```
<section itemscope itemtype="http://schema.org/BlogPosting">
  <meta content="https://example.com/blog/hello" itemprop="url">
  ...
</section>
```

Bien:

```
<section itemscope itemtype="http://schema.org/BlogPosting">
  <link href="/blog/hello" itemprop="url">
  ...
</section>
```

### Usa el elemento `address` solamente para información de contacto

El elemento `address` es para direcciones de email, redes sociales, domicilio, número de teléfono y otros medios de contacto.

Mal:

```
<address>No rights reserved.</address>
```

Bien:

```
<address>Contact: <a href="https://twitter.com/hail2u_">Kyo Nagashima</a></address>
```

### Usa de forma apropiada el elemento `blockquote`

El contenido del elemento `blockquote` es una cita, no bloques de caracteres.

Mal:

```
<blockquote>For writing maintainable and scalable HTML documents.</blockquote>
```

Bien:

```
<blockquote>
  <p>For writing maintainable and scalable HTML documents.</p>
</blockquote>
```

### Usa el atributo `type` para elementos `ol`

Algunas veces el marcador es referenciado por los contenidos cercanos. Si cambias el tipo del marcador  
con el atributo `type`, estarás seguro ante esas referencias.

Mal:

```
<head>
  <style>
    .toc {
      list-style-type: upper-roman;
    }
  </style>
</head>
<body>
  <ol class="toc">
    <li>General</li>
    <li>The root Element</li>
    <li>Sections</li>
    ...
  </ol>
</body>
```

Bien:

```
<body>
  <ol type="I">
    <li>General</li>
    <li>The root Element</li>
    <li>Sections</li>
    ...
  </ol>
</body>
```

### Usa el elemento `main`

El elemento `main` puede ser usado para envolver contenido.

Mal:

```
<div id="content">
  ...
</div>
```

Bien:

```
<main>
  ...
</main>
```

### Evita el elemento `div` tanto como sea posible

El elemento `div` es el último recurso.

Mal:

```
<div class="chapter">
  ...
</div>
```

Bien:

```
<section>
  ...
</section>
```

## Semántica a nivel de texto

### No dividas un enlace que puede ser agrupado

El elemento `a` puede envolver a casi todos los elementos (excepto elementos interactivos como  
controles de un formulario y el mismo elemento `a`).

Mal:

```
<h1><a href="https://whatwg.org/">WHATWG</a></h1>

<p><a href="https://whatwg.org/">A community maintaining and evolving HTML since 2004.</a></p>
```

Bien:

```
<a href="https://whatwg.org/">
  <h1>WHATWG</h1>

  <p>A community maintaining and evolving HTML since 2004.</p>
</a>
```

### Usa el atributo `download` para descargar un recurso

Esto forzará a los navegadores a descargar el recurso vinculado al almacenamiento.

Mal:

```
<a href="/downloads/offline.zip">offline version</a>
```

Bien:

```
<a download href="/downloads/offline.zip">offline version</a>
```

### Usa los atributos `rel`, `hreflang`, y `type` si es necesario

Estas pistas ayudan a las aplicaciones a manejar el recurso vinculado.

Mal:

```
<a href="/ja/pdf">Japanese PDF version</a>
```

Bien:

```
<a href="/ja/pdf" hreflang="ja" rel="alternate" type="application/pdf">Japanese PDF version</a>
```

### Pon un texto claro en los enlaces

El texto de un enlace debe describir el recurso vinculado.

Mal:

```
<p><a href="/pdf" rel="alternate" type="application/pdf">Click here</a> to view PDF version.</p>
```

Bien:

```
<p><a href="/pdf" rel="alternate" type="application/pdf">PDF version</a> is also available.</p>
```

```
<ruby>HTML<rp> (</rp><rt>えいちてぃーえむえる</rt><rp>) </rp></ruby>
```

### Añade el atributo `datetime` al elemento `time` si usa formatos no reconocibles por la máquina

Cuando el atrubuto `datetime` no está presente, el formato del contenido del elemento `time` es restringido.

Mal:

```
<time>Dec 19, 2014</time>
```

Bien:

```
<time datetime="2014-12-19">Dec 19, 2014</time>
```

### Especifica el lenguaje del código con un atributo `class` con prefijo `language-`

No es una manera muy formal, pero la especificación lo menciona así.

Mal:

```
<code>&lt;!DOCTYPE html&gt;</code>
```

Bien:

```
<code class="language-html">&lt;!DOCTYPE html&gt;</code>
```

### Mantén el elemento `kbd` tan simple como sea posible

Anidar el elemento `kbd` es difícil para los humanos.

Mal:

```
<kbd><kbd>Ctrl</kbd>+<kbd>F5</kbd></kbd>
```

Bien:

```
<kbd>Ctrl+F5</kbd>
```

### Evita el elemento `span` tanto como sea posible

El elemento `span` es el último recurso.

Mal:

```
HTML <span class="best">Best</span> Practices
```

Bien:

```
HTML <em>Best</em> Practices
```

### Usa un salto de línea al usar el elemento `br`

Debería ser necesario cuando el elemento `br` es usado.

Mal:

```
<p>HTML<br>Best<br>Practices</p>
```

Bien:

```
<p>HTML<br>
Best<br>
Practices</p>
```

### No uses el elemento `br` solo con fines de presentación

El elemento `br` es para dar saltos de línea en el contenido.

Mal:

```
<p><label>Rule name: <input name="rule-name" type="text"></label><br>
<label>Rule description:<br>
<textarea name="rule-description"></textarea></label></p>
```

Bien:

```
<p><label>Rule name: <input name="rule-name" type="text"></label></p>
<p><label>Rule description:<br>
<textarea name="rule-description"></textarea></label></p>
```

## Ediciones

### No coloques elementos `ins` y `del` sobre otros elementos

Los elementos no pueden desbordar otros elementos.

Mal:

```
<p>For writing maintainable and scalable HTML documents.<del> And for mental stability.</p>

<p>Don’t trust!</p></del>
```

Bien:

```
<p>For writing maintainable and scalable HTML documents.<del> And for mental stability.</del></p>

<del><p>Don’t trust!</p></del>
```

## Contenido incrustado

### Usa un elemento `img` alternativo para el elemento `picture`

El soporte del elemento `picture` aún no es bueno.

Mal:

```
<picture>
  <source srcset="/img/logo.webp" type="image/webp">
  <source srcset="/img/logo.hdp" type="image/vnd.ms-photo">
  <source srcset="/img/logo.jp2" type="image/jp2">
  <source srcset="/img/logo.jpg" type="image/jpg">
</picture>
```

Bien:

```
<picture>
  <source srcset="/img/logo.webp" type="image/webp">
  <source srcset="/img/logo.hdp" type="image/vnd.ms-photo">
  <source srcset="/img/logo.jp2" type="image/jp2">
  <img src="/img/logo.jpg">
</picture>
```

### Añade el atributo `alt` al elemento `img` si es necesario

El atributo `alt` ayuda a aquellos que no pueden procesar imágenes o tienen  
la carga de imágenes deshabilitada.

Mal:

```
<img src="/img/logo.png">
```

Bien:

```
<img alt="HTML Best Practices" src="/img/logo.png">
```

### Usa el atributo `alt` vacío de ser posible

Si la imagen es suplementaria, hay contenido equivalente cerca de ella.

Mal:

```
<img alt="Question mark icon" src="/img/icon/help.png"> Help
```

Bien:

```
<img alt="" src="/img/icon/help.png"> Help
```

### Omite el atributo `alt` de ser posible

A veces no se sabe qué texto es adecuado para el atributo `alt`.

Mal:

```
<img alt="CAPTCHA" src="captcha.cgi?id=82174">
```

Bien:

```
<img src="captcha.cgi?id=82174" title="CAPTCHA">
(Si no puedes ver la imagen, puedes usar un <a href="?audio">audio</a> de prueba en su lugar.)
```

### Elemento `iframe` vacío

Hay restricciones para su contenido. Tenerlo vacío es seguro siempre.

Mal:

```
<iframe src="/ads/default.html">
  <p>If your browser support inline frame, ads are displayed here.</p>
</iframe>
```

Bien:

```
<iframe src="/ads/default.html"></iframe>
```

### Marca el contenido del elemento `map`

Este contenido se presenta a los lectores de pantalla.

Mal:

```
<map name="toc">
  <a href="#general">General</a>
  <area alt="General" coords="0, 0, 40, 40" href="#General"> |
  <a href="#the_root_element">The root element</a>
  <area alt="The root element" coords="50, 0, 90, 40" href="#the_root_element"> |
  <a href="#sections">Sections</a>
  <area alt="Sections" coords="100, 0, 140, 40" href="#sections">
</map>
```

Bien:

```
<map name="toc">
  <p>
    <a href="#general">General</a>
    <area alt="General" coords="0, 0, 40, 40" href="#General"> |
    <a href="#the_root_element">The root element</a>
    <area alt="The root element" coords="50, 0, 90, 40" href="#the_root_element"> |
    <a href="#sections">Sections</a>
    <area alt="Sections" coords="100, 0, 140, 40" href="#sections">
  </p>
</map>
```

### Proporciona contenido alternativo para los elementos `audio` o `video`

El contenido alternativo es necesario para elementos recién introducidos en HTML.

Mal:

```
<video>
  <source src="/mov/theme.mp4" type="video/mp4">
  <source src="/mov/theme.ogv" type="video/ogg">
  ...
</video>
```

Bien:

```
<video>
  <source src="/mov/theme.mp4" type="video/mp4">
  <source src="/mov/theme.ogv" type="video/ogg">
  ...
  <iframe src="//www.youtube.com/embed/..." allowfullscreen></iframe>
</video>
```

## Tablas

### Escribe una celda por línea

Las líneas largas son difíciles de leer.

Mal:

```
<tr>
  <td>General</td><td>The root Element</td><td>Sections</td>
</tr>
```

Bien:

```
<tr>
  <td>General</td>
  <td>The root Element</td>
  <td>Sections</td>
</tr>
```

### Usa el elemento `th` para las celdas de cabecera

No hay razón para evitarlo.

Mal:

```
<table>
  <thead>
    <tr>
      <td><strong>Element</strong></td>
      <td><strong>Empty</strong></td>
      <td><strong>Tag omission</strong></td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong><code>pre</code></strong></td>
      <td>No</td>
      <td>Neither tag is omissible</td>
    </tr>
    <tr>
      <td><strong><code>img</code></strong></td>
      <td>Yes</td>
      <td>No end tag</td>
    </tr>
  </tbody>
</table>
```

Bien:

```
<table>
  <thead>
    <tr>
      <th>Element</th>
      <th>Empty</th>
      <th>Tag omission</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th><code>pre</code></th>
      <td>No</td>
      <td>Neither tag is omissible</td>
    </tr>
    <tr>
      <th><code>img</code></th>
      <td>Yes</td>
      <td>No end tag</td>
    </tr>
  </tbody>
</table>
```

## Formularios

### Envuelve los controles del formilario con el elemento `label`

El elemento `label` ayuda a enfocar el elemento del formulario.

Mal:

```
<p>Query: <input name="q" type="text"></p>
```

Bien:

```
<p><label>Query: <input name="q" type="text"></label></p>
```

### Omite el atributo `for` de ser posible

El elemento `label` puede contener a algunos elementos del formulario.

Mal:

```
<label for="q">Query: </label><input id="q" name="q" type="text">
```

Bien:

```
<label>Query: <input name="q" type="text"></label>
```

### Usa un atributo `type` apropiado para el elemento `input`

Con un `type` apropiado, los navegadores brindan funciones extra a los elementos `input`.

Mal:

```
<label>Search keyword: <input name="q" type="text"></label>
```

Bien:

```
<label>Search keyword: <input name="q" type="search"></label>
```

### Añade el atributo `value` a los elementos `input type="submit"`

El texto por defecto para el botón de enviar no está estandarizado  
en distintos navegadores e idiomas.

Mal:

```
<input type="submit">
```

Bien:

```
<input type="submit" value="Search">
```

### Añade el atributo `title` a elementos `input` que tienen un atributo `pattern`

Si el texto introducido no es aceptado con el atributo `pattern`, el valor del atributo `title`  
se mostrará como una guia.

Mal:

```
<input name="security-code" pattern="[0-9]{3}" type="text">
```

Bien:

```
<input name="security-code" pattern="[0-9]{3}" title="A security code is a number in three figures." type="text">
```

### No uses el atributo `placeholder` como etiqueta

El elemento `label` es para etiquetar, el elemento `placeholder` es para mostrar una pista breve.

Mal:

```
<input name="email" placeholder="Email" type="text">
```

Bien:

```
<label>Email: <input name="email" placeholder="john.doe@example.com" type="text"></label>
```

### Añade el atributo `max` al elemento `progress`

Con el atributo `max`, el atributo `value` puede ser escrito en un formato sencillo.

Mal:

```
<progress value="0.5"> 50%</progress>
```

Bien:

```
<progress max="100" value="50"> 50%</progress>
```
