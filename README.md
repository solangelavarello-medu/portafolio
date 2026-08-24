# Portafolio · Solange Lavarello

Portafolio dirigido a posiciones de **Senior Product Designer**. Cuatro casos de estudio
—Belcorp, BID, Isapre Esencial y SIGO— elegidos porque cubren ángulos distintos de
seniority, no porque sean los más vistosos.

Todo el sitio es **un solo archivo**: `index.html`. No hay build, no hay dependencias,
no hay `node_modules`. Se abre con doble clic y funciona.

---

## Cómo verlo

Abrir `index.html` en el navegador. Alcanza.

Si el navegador se pone difícil con algo al abrirlo como archivo local, levantar un
servidor de un comando en la carpeta del repo y entrar a `http://localhost:8000`:

```bash
python3 -m http.server 8000
```

Python 3 ya viene en cualquier Mac.

---

## Cómo está armado

Un archivo, seis vistas, ruteo por hash. No hay recarga de página entre secciones.

| Ruta | Qué es |
|---|---|
| `#/` | Home — hero, los 4 casos, competencias, contacto |
| `#/belcorp` | Caso Belcorp — Catálogo Virtual |
| `#/bid` | Caso BID — Unidad Fiduciaria, 26 países |
| `#/isapre` | Caso Isapre Esencial |
| `#/sigo` | Caso SIGO — Ministerio de Salud de Chile |
| `#/about` | Sobre mí — trayectoria, formación, idiomas |

El `<script>` del final oculta y muestra las secciones según el hash. Para agregar un
caso nuevo hay que sumar la `<section class="page" id="page-X">` y el `'X'` al array
`pages`.

### Idiomas

El sitio está en español e inglés. Cada bloque de texto existe dos veces en el marcado,
marcado con `data-lang="es"` o `data-lang="en"`, y el script muestra solo el idioma
activo. El selector vive arriba a la derecha.

El idioma se elige así: primero lo que la persona haya escogido antes (queda en
`localStorage`), y si no hay nada guardado, se mira el idioma del navegador. Español si
empieza por `es`, inglés en cualquier otro caso.

Al traducir o corregir un texto hay que tocar **las dos versiones**. Si una queda sin su
par, ese contenido desaparece al cambiar de idioma.

### Diseño

- **Tipografías:** Newsreader (display), Public Sans (texto), IBM Plex Mono (etiquetas y
  metadata). Se cargan desde Google Fonts.
- **Color:** petróleo sobre papel verde-grisáceo. Todo pasa por variables CSS en `:root`,
  con tema claro y oscuro. Ningún color está escrito directo en un componente.
- **Diagramas:** SVG inline, escritos a mano, sin librerías. Usan `currentColor` y las
  variables del tema, así que se leen igual en claro y en oscuro. Cada uno existe en las
  dos versiones de idioma, con los textos del SVG traducidos.
- **Móvil:** el layout colapsa a una columna. Los diagramas no se encogen hasta volverse
  ilegibles, se desplazan en horizontal dentro de su propio marco.

---

## La regla editorial

> **Nada de lo que dice este sitio es inventado.**

Toda cifra, decisión, restricción y resultado sale de lo que reporté directamente. Lo que
es una estimación no medida está marcado como tal. Lo que fue trabajo de equipo está
escrito en lenguaje de equipo ("co-lideré", "decidimos"), no atribuido a mí sola.

Esto aplica a cualquier cambio futuro: si falta contenido, el espacio queda vacío. No se
rellena con texto genérico.

---

## Espacios reservados

Hay 11 bloques marcados como pendientes a lo largo del sitio, con borde punteado y la
etiqueta "espacio reservado" o "contenido pendiente". Son intencionales: marcan lo que
falta en vez de taparlo.

Para ocultarlos todos antes de compartir el sitio, agregar al CSS:

```css
.reservado{display:none}
```

Quitar esa línea los vuelve a mostrar.

### Qué falta

- **Bio narrativa** y bloque "cómo trabajo" del About.
- **Resumen de competencias** (Home y arriba de cada caso) — falta definir el formato.
- **Testimonios** — requieren permiso explícito de cada persona antes de publicarse.
- **Galerías** de Belcorp, Isapre Esencial y SIGO — falta confirmar qué material visual
  se puede recuperar.
- **Títulos definitivos** de Belcorp, Isapre Esencial y SIGO (los actuales son
  provisionales; el del BID ya está cerrado).

### Por validar antes de publicar

- Que no haya restricción contractual sobre citar las cifras de Belcorp, aunque sean
  públicas por Altimea.
- El número exacto de países del BID con configuración específica (hoy dice "cuatro o
  cinco", de memoria).
- Si Belcorp fue empleador directo o fue vía Altimea — el CV y el caso dicen cosas
  distintas.

---

## Confidencialidad

El caso del **BID** no muestra capturas, flujos ni datos reales, por política de privacidad
del banco. Sus diagramas son ilustrativos. La página lleva el aviso correspondiente.

Si en algún momento se necesita bloqueo por contraseña a nivel de caso, este sitio no
puede hacerlo solo: hay que servirlo desde algo que soporte autenticación.
