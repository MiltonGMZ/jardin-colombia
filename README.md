# Jardín Colombia — sitio web (Astro)

Sitio inspirado en el lenguaje visual de [PoliNations](https://www.polinations.com/)
(tipografía enorme, video de fondo, secciones a página completa, color con
carácter) pero construido 100% con el contenido real de
[jardincolombiasas.com](https://jardincolombiasas.com/): exportación de
flores, venta nacional de arreglos, plantas de temporada y eventos.

## Cómo correrlo

```bash
npm install
npm run dev       # http://localhost:4321
npm run build      # genera /dist listo para publicar
npm run preview    # sirve /dist localmente
```

Requiere Node 18+.

## Estructura

```
src/
  layouts/Layout.astro      ← <head>, fuentes, scroll-reveal global
  components/
    Nav.astro                ← barra fija + sello giratorio + menú móvil
    Hero.astro                ← video de fondo a página completa
    About.astro                ← "Quiénes somos" + collage de fotos
    ExportRoute.astro          ← ruta animada Bogotá → Curazao/Aruba/Panamá/USA
    SeasonalBouquets.astro     ← carrusel infinito de campañas de temporada
    NationalSale.astro         ← venta nacional de arreglos + proceso
    Plants.astro                ← plantas de temporada + cuidados
    Events.astro                 ← galería de eventos
    CTAFooter.astro               ← CTA final "Florece aquí" + pie de página
  pages/index.astro           ← arma todas las secciones
  styles/global.css            ← tokens de marca (color, tipografía, botones)
public/
  media/images/                ← 26 imágenes placeholder (ver abajo)
  media/videos/                ← aquí va hero.mp4
  favicon.svg
```

## Reemplazar imágenes y videos

Todas las imágenes son **placeholders generados** con los colores de marca
y una etiqueta con el nombre del archivo, para que puedas ver la
composición final antes de poner las fotos reales. Solo tienes que
**reemplazar el archivo manteniendo el mismo nombre** (o cambiar la ruta en
el componente si prefieres otro nombre):

| Sección | Archivo(s) a reemplazar |
|---|---|
| Hero (video de fondo) | `public/media/videos/hero.mp4` + `public/media/images/hero-poster.jpg` |
| Quiénes somos | `quienes-somos-1.jpg`, `quienes-somos-2.jpg`, `quienes-somos-3.jpg` |
| Bouquets de temporada | `san-valentin.jpg`, `dia-de-mujer.jpg`, `dia-de-la-madre.jpg`, `halloween.jpg`, `accion-de-gracias.jpg`, `navidad.jpg` |
| Venta nacional | `ramo.jpg`, `ramo-1.jpg`, `ramo-2.jpg`, `ramo-3.jpg` |
| Plantas de temporada | `orquidea.jpg`, `planta.jpg`, `ponsettia.jpg`, `bromelia.jpg`, `suculenta.jpg` |
| Eventos | `grados.jpg`, `toyota.jpg`, `playa.jpg`, `playa-2.jpg`, `15-anos.jpg`, `primera-comunion.jpg` |
| Meta / redes sociales | `og-cover.jpg` (1200×630) |

**Recomendaciones para el video del hero:** MP4, sin audio, 10–20s en loop,
1920×1080 o similar, peso ideal < 8MB para que cargue rápido (puedes
comprimirlo con Handbrake o `ffmpeg -crf 28`).

## Marca / tokens (en `src/styles/global.css`)

- `--ink #0F1B12` — texto y fondos oscuros
- `--paper #FAF7F2` — fondo base
- `--rose #E8317B` — acento principal (CTAs, marca)
- `--mango #FF9F1C` — acento cálido de temporada
- `--forest #1F4D2C` — verde de cultivo/confianza
- `--lilac #D9C9F0` — fondo suave para "Quiénes somos"

Tipografías: **Fraunces** (titulares), **Space Grotesk** (cuerpo/UI),
**Space Mono** (etiquetas, códigos de exportación).

## Contacto usado en los botones

WhatsApp: `https://wa.me/+573208233636` — cambia el número en
`Nav.astro`, `Hero.astro`, `SeasonalBouquets.astro`, `NationalSale.astro`
y `CTAFooter.astro` si cambia.

## Publicar

El sitio es estático — funciona en Vercel, Netlify, Cloudflare Pages o
cualquier hosting estático corriendo `npm run build` y sirviendo `/dist`.
