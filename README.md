# App de Facturas

**Master your body, mind and money.** (eslogan de Balmore; se muestra en inglés en ambos idiomas).

App gratis de Balmore Hernandez (@BalmoreHernandez.sv) para crear facturas simples, guardarlas en PDF y saber quién debe. En español con versión en inglés (botón ES/EN). Se publica en `https://balmorehernandez.com/invoices/` (GitHub Pages, repo `BalmoreHernandez/invoices`, sin CNAME).

Pestañas: Inicio, Facturas, Clientes, Precios y Más.

- **Inicio:** total por cobrar, vencido, cobrado este mes y facturas pendientes.
- **Facturas:** crear, editar, duplicar, marcar pagada (fecha, forma de pago, número de cheque) y guardar en PDF desde la pantalla de impresión.
- **Clientes:** datos del cliente, saldo y estado de cuenta imprimible.
- **Precios:** lista de servicios o productos para llenar una factura sin volver a escribir.
- **Más:** datos del negocio (logo, dirección, forma de pago, numeración, plazo e impuesto habituales), respaldo, ajustes y contacto.

Archivo principal: `index.html`. Es autocontenido (CSS, JS, fuentes e íconos dentro) y funciona sin internet. La única petición de red es el envío del formulario de contacto.

## Privacidad
Todo se guarda solo en el dispositivo (localStorage, clave `bh-invoices-v1`). No hay cuentas, base de datos ni analítica. Este repositorio es público: **nunca** pongas aquí datos de clientes, precios reales ni facturas. Cada negocio escribe sus datos en su propio teléfono y los mueve con "Guardar respaldo" / "Importar respaldo" (`.json`).

No genera facturas electrónicas fiscales (DTE, CFDI u otras); la app lo dice en el pie y en las preguntas frecuentes.

## Dónde editar (todo dentro de `index.html`, bloque `CONFIG`)
- `BRAND_NAME`: nombre que aparece en el título y el pie.
- `APP_URL`: dirección pública de la app.
- `WHATSAPP_NUMBER` y `WHATSAPP_TEXT` (es/en): enlace "Trabaja conmigo".
- `LEAD_FORM_URL`: URL del Web App de Google Apps Script (el mismo de las otras apps). Vacía = el formulario abre WhatsApp.
  - Envío: `fetch(url, {method:'POST', mode:'no-cors', body: URLSearchParams})` con `nombre`, `email`, `whatsapp`, `objetivo`, `idioma`, `fuente`.
  - Honeypot `website`: si viene lleno, no se envía nada.
- `LEAD_SOURCE`: `app-invoices` (columna "Fuente" de la hoja Leads).
- `SOCIAL`: Instagram, TikTok y Facebook.
- `CURRENCIES`: monedas que se ofrecen.
- `TERMS`: plazos de pago en días (0 = al recibir).
- `PAY_METHODS`: formas de pago al registrar un cobro.
- `LOGO_MAX_PX`: tamaño máximo al que se reduce el logo del negocio.
- Textos de la app en `I18N` (es/en, mismas claves) y textos del documento impreso en `DOC` (es/en).
- Si cambias `index.html` después de publicar, sube la versión de `CACHE` en `sw.js`.

## Registro de cambios
- 2026-10-07 — Primera versión (vista previa, sin publicar) — Nico (Claude Cowork)
