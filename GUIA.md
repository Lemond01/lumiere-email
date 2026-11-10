# Guía de uso · LUMIÈRE

Todo lo necesario para configurar, enviar y revisar el email. Para conocer el proyecto, ve al [README](README.md).

---

## Carpeta

```
lumiere-email-v2/
├── index.html               ← el email (CSS inline)
├── plain-text-version.txt   ← versión en texto plano
├── README.md                ← presentación del proyecto
├── GUIA.md                  ← esta guía
├── docs/                    ← imágenes del README
└── images/                  ← elementos decorativos del email (PNG, 2x para pantallas retina)
```

---

## Qué configurar antes de enviar

| Placeholder | Qué poner |
|---|---|
| `https://www.lumiere.example/experiencias` | Página de experiencias (botón principal) |
| `https://www.lumiere.example/cotizar` | Página o formulario de cotización (lleva `?paquete=…`) |
| `5210000000000` | Tu WhatsApp: lada de país + número, solo dígitos (aparece en 4 enlaces) |
| `hola@lumiere.example` | Correo de contacto |
| `+52 (000) 000 0000` y `tel:+520000000000` | Teléfono |
| `https://www.instagram.com/tu-usuario` | Instagram |
| `[Dirección del negocio, Ciudad, Estado, C.P.]` | Dirección física (la piden las leyes anti-spam) |
| `{{WEB_VERSION_URL}}` | Merge tag "ver en navegador" (Mailchimp: `*\|ARCHIVE\|*`) |
| `{{UNSUBSCRIBE_URL}}` | Merge tag de baja (ver abajo) |

**Darse de baja:**

| Plataforma | Merge tag |
|---|---|
| Mailchimp | `*\|UNSUB\|*` |
| Brevo | `{{ unsubscribe }}` |
| HubSpot | `{{ unsubscribe_link }}` |

**Asunto sugerido:** `Tienes una invitación ✉`
**Preheader:** `Haz que tu celebración se recuerde para siempre con una experiencia fotográfica que tus invitados van a amar.`

> Todo lo que pongas en el HTML lo puede ver quien reciba el correo. Usa datos del negocio (correo, teléfono y dirección), no personales.

---

## Cómo publicar las imágenes decorativas (importante)

En `index.html` las imágenes decorativas usan rutas relativas (`images/…`). Así puedes ver el email abriendo el archivo en tu navegador. Para **enviarlo**, esas imágenes tienen que estar en internet. Hay tres opciones:

1. **Mailchimp (la más fácil):** Crear campaña → *Code your own* → **Import zip**. Sube el `.zip` del proyecto; Mailchimp aloja las imágenes y actualiza las rutas por ti.
2. **Brevo u otra plataforma:** sube los PNG de `images/` a su biblioteca de imágenes. Copia la URL base y reemplaza `src="images/` por `src="https://tu-url/`.
3. **GitHub Pages:** sube la carpeta a un repositorio, activa Pages y reemplaza `src="images/` por `src="https://tu-usuario.github.io/lumiere-email/images/`.

Si copias el HTML directo a Gmail sin publicar las imágenes, las fotos sí se verán pero los adornos no.

---

## Cómo enviarte una prueba

1. Crea una cuenta gratis en Mailchimp.
2. Ve a Campañas → Email → *Code your own* → **Import zip** y sube el zip.
3. Escribe el asunto y el preheader. Pega `plain-text-version.txt` en la versión de texto plano.
4. Reemplaza los placeholders (tabla de arriba).
5. Usa **Preview and test → Send a test email** a tu correo. Si puedes, revísalo en Gmail, Outlook/Hotmail y en el celular.

## Lista de revisión por cliente

| Revisión | Gmail web | Gmail app | Outlook escritorio | Outlook web | Apple Mail / iPhone |
|---|---|---|---|---|---|
| Se ve el sobre con el sello | ☐ | ☐ | ☐ | ☐ | ☐ |
| Se ve LUMIÈRE en la solapa del sobre de abajo | ☐ | ☐ | ☐ | ☐ | ☐ |
| Fotos con papel rasgado | ☐ | ☐ | ☐ | ☐ | ☐ |
| Letra manuscrita (imágenes) visible | ☐ | ☐ | ☐ | ☐ | ☐ |
| Columnas apiladas en celular | — | ☐ | — | — | ☐ |
| Botones de WhatsApp y correo funcionan | ☐ | ☐ | ☐ | ☐ | ☐ |
| Se entiende con imágenes bloqueadas | ☐ | ☐ | ☐ | ☐ | ☐ |

**Diferencias esperadas (no son errores):**
- En **Outlook de escritorio** los botones se ven rectangulares y la tipografía es Georgia.
- En **Gmail** la tipografía también es Georgia (Gmail no carga fuentes web).
- En modo oscuro algunos clientes pueden invertir colores.

**Litmus o Email on Acid** (de pago, con prueba gratis) muestran capturas del email en decenas de clientes a la vez. Sirven para revisar Outlook si no lo tienes instalado.

> La vista previa en el navegador no garantiza cómo se verá en un cliente de correo, porque cada uno elimina o reescribe partes del CSS. Hay que probar enviándolo.

## Control de calidad hecho

- Vista en navegador a 680 px y 390 px: sin scroll horizontal, columnas apiladas en celular.
- Las 7 fotos cargan desde Pexels y el papel rasgado se ve encima de las fotos.
- Vista con imágenes bloqueadas: el texto alternativo y todo el contenido se leen.
- Contraste revisado en todas las combinaciones de color.

No se ha probado en clientes de correo reales; eso te toca al enviarte la prueba.

---

## Dirección de arte

Está basada en tres referencias de invitaciones:

| Referencia | Cómo se tradujo al email |
|---|---|
| Sobre vino con sello dorado | La apertura es la solapa de un sobre vino con sello de lacre "L" y ramitas de nube (gypsophila). |
| Nombres en mayúsculas con "y" manuscrita | Titular: **CADA MOMENTO** — *merece* — **SER RECORDADO**, con líneas a los lados. |
| Fecha manuscrita bajo los nombres | "*tu día · tu gente · tu historia*". |
| Foto con bordes de papel rasgado | La foto principal y la de "pequeños momentos" tienen bordes rasgados, y las secciones cambian de color con un corte de papel rasgado. |
| "Our story" con polaroids y línea de tiempo | Sección "*así se vive*": antes, durante y después, con polaroids con cinta washi. |
| "The details" con íconos de línea | Sección "*para cada* CELEBRACIÓN" con íconos de anillos, globo y portafolio. |
| Pantallas de detalles con tarjetas | Colecciones en tarjetas con arco: la central es color vino y lleva sello. |
| "Kindly RSVP" con casillas | "FAVOR DE CONFIRMAR": tarjeta con casillas que en realidad son enlaces a WhatsApp con un mensaje ya escrito. |
| "We can't wait…", firmado | Cierre "*¡no podemos esperar a celebrar contigo!*" y "*con cariño,*". |
| Sobre abierto con la carta dentro | Arriba, la solapa con el sello; abajo, el bolsillo del sobre (solapas laterales en V + solapa inferior con **LUMIÈRE · Experiencias fotográficas**): el contenido es la carta que sale del sobre. |
| Fondos beige con sombras de hojas | Fondo de página con luz suave y sombras de hojas (`images/bg_page.jpg`, hecho para este proyecto). Si un cliente no muestra fondos, queda el color beige `#EDE3D4`. |

**Tipografía**
- **Cormorant Garamond** se carga desde Google Fonts. Se ve en Apple Mail e iOS; en Gmail y Outlook se reemplaza automáticamente por **Georgia**.
- La letra manuscrita (**Pinyon Script**) está en imágenes PNG con texto alternativo. Así se ve igual en todos los clientes.

---

## Decisiones técnicas

- **Tablas + CSS inline.** Outlook usa el motor de Word y no entiende Flexbox ni Grid. Todos los estilos importantes van en el atributo `style`.
- **Media query solo como mejora.** En celular las columnas se apilan, las polaroids se centran y las tarjetas de colección se muestran una debajo de otra.
- **Papel rasgado sobre fotos.** La foto va como *fondo* de la celda y los bordes rasgados (PNG con transparencia) van encima:
  - en Outlook se usa VML;
  - si un cliente no muestra fondos, se ve color champagne con los bordes rasgados, y el diseño no se rompe.
- **Marca sobre el sobre.** "LUMIÈRE · Experiencias fotográficas" es texto HTML encima de la solapa inferior:
  - la parte de arriba del bolsillo (`envelope_pocket_top.png`) es el fondo de la celda (VML en Outlook);
  - un espaciador transparente (`spacer_pocket.png`) baja el texto y escala con el ancho en celular;
  - las esquinas y la sombra (`envelope_pocket_bottom.png`) van como imagen normal debajo;
  - si un cliente no muestra fondos, se ve color vino con el texto marfil encima.
- **Esquinas redondeadas del sobre.** Las esquinas son transparentes dentro de los PNG (`envelope.png` arriba, `envelope_pocket_bottom.png` abajo). Por eso la solapa de arriba va fuera de la tabla marfil y sin color de fondo: así se ve el fondo de la página en las esquinas.
- **Sin JavaScript ni formularios.** Los clientes de correo los bloquean. Las "casillas" del RSVP son enlaces de WhatsApp (`wa.me`) con un texto distinto según el tipo de evento.
- **Accesibilidad.**
  - Todas las imágenes tienen `alt`; las decorativas usan `alt=""`.
  - Las fotos de fondo llevan `role="img"` y `aria-label`.
  - La palabra manuscrita de cada título está en imagen con su `alt`, pero el título real (h1/h2/h3) es texto HTML.
  - Contraste AA en todos los textos: vino sobre marfil 11.3:1, gris sobre marfil 6.3:1, marfil sobre vino 11.3:1, dorado sobre la solapa del sobre 5.3:1.

---

## Imágenes

**Fotos** (Pexels, licencia libre, URL absolutas HTTPS):

| Uso | ID |
|---|---|
| Foto principal: neón "Better Together" | 15291907 |
| Polaroid "los detalles" | 13788485 |
| Polaroid "al instante" | 6030108 |
| Polaroid "para siempre" | 4550433 |
| XV años y cumpleaños | 6519369 |
| Eventos de marca | 27381456 |
| Pequeños momentos | 9342943 |

**Elementos decorativos** (carpeta `images/`, creados para este proyecto): solapa y bolsillo del sobre, fondo de página, sellos, papel rasgado, letra manuscrita, cinta, arcos, ramitas e íconos.

---

## Requisitos de la actividad (EBAC)

| Requisito | Dónde |
|---|---|
| Estructura HTML básica | `<!DOCTYPE html>`, `<head>`, `<body>` |
| Header con logo y título | Sobre con sello "L" + titular principal |
| Cuerpo con texto e imágenes | Todas las secciones |
| Llamado a la acción | "Conoce nuestras experiencias" y "Escríbenos por WhatsApp" |
| Footer con contacto y copyright | Marca en la solapa del sobre; contacto y copyright debajo, sobre el fondo de página |
| CSS inline | En todos los elementos |
| Diseño atractivo y moderno | Suite de invitación de boda |
| Pruebas | Secciones "Cómo enviarte una prueba" y "Lista de revisión" de esta guía |
