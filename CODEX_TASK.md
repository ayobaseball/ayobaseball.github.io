# AYO Baseball Supply: tarea para Codex

Pega este archivo en Codex junto con `index.html`, `catalogo.csv` y `assets-manifest.csv`.
Claude ya aplicó la identidad visual y el catálogo de 20 referencias. Mejora el proyecto sin rehacer la arquitectura.

## Estado actual (verificado el 25-11-2026 con Playwright y Chrome)
- Página única y autocontenida (`index.html`), sin dependencias. Fuentes: Bebas Neue y Montserrat de Google Fonts (licencia OFL).
- 20 referencias en el array `P`. `priceCents: null` significa que el precio no está confirmado y se cotiza. `img: null` significa que la foto oficial está pendiente de autorización.
- Funciona: filtros por categoría, marca y nivel; búsqueda; orden; ficha con talla y mano (RHT/LHT); bolsa persistente en localStorage con ID estable `AYO-XXXXXX`; ticket wa.me con `encodeURIComponent`; formulario Academy; configurador AYO (vista previa ilustrativa).
- Pruebas que pasaron (23 de 23): 320, 375, 390 y 430 px sin scroll horizontal; filtros; validación de variantes; carrito; recarga; ID estable; codificación del enlace; validación del checkout y de Academy; sin errores de JavaScript.

## Tareas
1. Migra el proyecto a un repositorio (rama `feat/ayo-premium`), sin cambiar la experiencia. Si propones Astro o Next.js, justifícalo primero.
2. Saca el catálogo a `data/catalog.json`, generado a partir de `catalogo.csv`, con validación: SKU obligatorio, `priceCents` entero o null, `hand` booleano y tallas no vacías.
3. Fotos: lee `assets-manifest.csv`. Renderiza la foto solo si `permission_status=autorizado` y el archivo existe en `local_path`. Si no, mantén la tarjeta técnica actual. Añade un script que falle si una imagen autorizada no existe o no es WebP/AVIF. No descargues imágenes de terceros sin autorización.
4. Optimiza las imágenes autorizadas a WebP y AVIF (1200 px, sin alterar forma ni color) y con `width`/`height` para evitar CLS.
5. Número de WhatsApp empresarial configurable (`WA_PHONE` o variable de entorno). No marques ningún pedido como pagado.
6. Ejecuta lint, comprobación de tipos (si migras a TypeScript), Playwright en 320/375/390/430 px y escritorio, y Lighthouse con objetivo superior a 90. Entrega capturas y resultados reales. No declares éxito sin ejecutarlo.

## Pendiente de negocio (no inventar)
- Precios públicos, stock y número de WhatsApp: los da el dueño.
- Wilson A800: no figura en wilson.com; confirmar con el distribuidor o sustituir por el A700 11,5″.
- "Rawlings DLB3" no existe con ese nombre; decidir entre OLB3 (práctica) y ROLB1 (competición).
- Fotos oficiales: solicitar permiso al distribuidor autorizado de cada marca.
