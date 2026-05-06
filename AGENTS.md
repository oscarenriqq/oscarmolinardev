# AGENTS.md

Contexto para agentes que trabajen en este repositorio.

## Proyecto

Este repositorio contiene el sitio personal de Oscar Molinar, publicado como una landing/portfolio estático en Astro. El contenido principal está en español y presenta perfil, enlaces de contacto, proyectos, caja de herramientas y una galería de hobbies.

URL configurada del sitio: `https://oscarmolinar.dev`.

## Stack

- Astro 6 con componentes `.astro`.
- Tailwind CSS 4 mediante `@tailwindcss/vite`.
- Sitemap con `@astrojs/sitemap`.
- TypeScript configurado en modo estricto por `astro/tsconfigs/strict`.
- `typewriter-effect` para el texto animado del hero.
- Fuentes locales DM Mono en `public/fonts/`.

## Comandos

Ejecutar desde la raíz del proyecto:

- `npm install`: instala dependencias.
- `npm run dev`: inicia el servidor local de Astro.
- `npm run build`: genera el build de producción en `dist/`.
- `npm run preview`: previsualiza el build generado.
- `npm run astro -- --help`: ayuda del CLI de Astro.

No hay scripts de test, lint o format definidos actualmente en `package.json`.

## Estructura Relevante

- `src/pages/index.astro`: página principal del portfolio. Importa layout, galería y datos JSON.
- `src/layouts/Layout.astro`: HTML base, metadatos, favicon, sitemap, Google Analytics, carga global de estilos y lógica inicial de tema.
- `src/components/PhotoGallery.astro`: galería de imágenes usando `astro:assets`.
- `src/styles/global.css`: Tailwind, variante custom para dark mode, declaración de fuentes DM Mono y fuente global.
- `src/data/projects.json`: listado editable de proyectos mostrados en la página.
- `src/data/tools.json`: listado editable de tecnologías e iconos de la caja de herramientas.
- `src/assets/hobbies/`: imágenes optimizadas por Astro para la galería.
- `public/`: assets servidos directamente, como logos, iconos, favicon, robots y fuentes.
- `astro.config.mjs`: configuración de Astro, Tailwind vía Vite, sitemap y URL del sitio.

## Convenciones Del Proyecto

- Mantener el contenido visible en español.
- Preferir componentes `.astro` simples y datos estáticos en JSON cuando el contenido sea editable.
- Usar Tailwind en clases inline, siguiendo el estilo existente.
- Mantener la estética sobria y compacta: ancho máximo `max-w-3xl`, tipografía monoespaciada DM Mono, espaciados simples y bordes rectos.
- El dark mode se controla con la clase `.dark` en `document.documentElement` y la variante definida en `src/styles/global.css`.
- Los assets dentro de `public/` se referencian con rutas absolutas desde la raíz, por ejemplo `/logo_om.png`.
- Las imágenes importadas desde `src/assets/` deben pasar por `astro:assets` cuando se rendericen como imágenes optimizadas.

## Datos Editables

Para agregar o modificar proyectos, editar `src/data/projects.json` con objetos que mantengan esta forma:

```json
{
  "title": "Nombre",
  "description": "Descripción corta",
  "technologies": ["Astro", "Tailwind"],
  "link": "https://example.com",
  "date": "Mes Año"
}
```

Para agregar tecnologías, editar `src/data/tools.json` y asegurar que el icono exista en `public/icons/` o apunte a una ruta pública válida.

## Notas De Implementación

- `src/pages/index.astro` agrega `?ref=oscarmolinar.dev` a los enlaces de proyectos.
- El botón de tema guarda la preferencia en `localStorage` con la clave `theme`.
- `Layout.astro` incluye Google Analytics con el ID `G-JSR35SY8Y5`; no cambiarlo salvo petición explícita.
- Antes de entregar cambios visuales, ejecutar al menos `npm run build`.
- Si se inicia servidor local para revisión visual, Astro usa normalmente `http://localhost:4321`.

## Cuidado Con

- No introducir frameworks de frontend adicionales sin necesidad clara; el sitio está pensado como Astro estático.
- No mover imágenes públicas a `src/assets/` sin actualizar sus referencias.
- No eliminar fuentes locales ni logos usados por el layout y el selector de tema.
- Revisar responsive en móvil y escritorio cuando se toque la navegación, el hero o la galería.
