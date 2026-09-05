# DSWF_2A_2C26_Desarrollo-de-Sistemas-Web-Front-End-TP1

## Trabajo Práctico Grupal 1

### Proyecto web en equipo · HTML, CSS y JavaScript

Este es el primer trabajo práctico grupal del curso de Desarrollo de Sistemas Web Front End. El objetivo es construir un sitio web grupal con una portada, perfiles individuales, navegación interna y una bitácora que documente el proceso de trabajo en equipo.

---

### Integrantes del Equipo

- **Leandro Maselli** (Responsable de Estructura y Bases del Proyecto): [github.com/leoroan](https://github.com/leoroan)
- **Javier Canteros**: [github.com/USUARIO-javier](https://github.com/USUARIO-javier) <!-- TODO: pegar el perfil real -->
- **Maximiliano Quinteros**: [github.com/USUARIO-maximiliano](https://github.com/USUARIO-maximiliano) <!-- TODO: pegar el perfil real -->
- **Damián Pelisare**: [github.com/USUARIO-damian](https://github.com/USUARIO-damian) <!-- TODO: pegar el perfil real -->
- **Nidia Elías**: [github.com/USUARIO-nidia](https://github.com/nidia-elias) <!-- TODO: pegar el perfil real -->

> ⚠️ **Pendiente del equipo:** reemplazar cada `USUARIO-...` por el link real de GitHub de cada integrante (ej. `[github.com/leoroan](https://github.com/leoroan)`). Los cuatro perfiles restantes figuran como placeholder.

---

### Tecnologías Utilizadas

- HTML5
- CSS (solo Bootstrap 5.3 y sus utilidades)
- JavaScript (ES6+)
- Bootstrap 5.3 (CDN oficial)
- Bootstrap Icons (CDN oficial)

---

### Estructura de Archivos y Carpetas

```
├── index.html               → Portada
├── member1.html             → Perfil Leandro Maselli
├── member2.html             → Perfil Javier Canteros
├── member3.html             → Perfil Maximiliano Quinteros
├── member4.html             → Perfil Damián Pelisare
├── member5.html             → Perfil Nidia Elias
├── bitacora.html            → Bitácora de desarrollo
├── "condiciones del proyecto 1.md"
├── components/
│  └── navbar.html           → fragmento HTML del navbar (única fuente de verdad)
├── css/
│  └── style.css             → estilos mínimos + breakpoints 400/900/1200
├── js/
│  ├── main.js               → interactividad de portada y perfiles
│  └── components/
│     └── general-navbar.js  → Web Component <general-navbar>
└── img/
   ├── favicon.ico
   ├── yo_para_gmail.png
   └── capturas/             → capturas de pantalla para este README (sección Funciones JS)
```

---

### Guía de Estilos

#### Componente Reutilizable: Navbar General (`<general-navbar>`)

Para evitar repetir el código del navbar en cada vista, la navegación se centralizó en un **Web Component** reutilizable mediante JavaScript:

- **`components/navbar.html`**: fragmento HTML único que define la estructura del navbar (la "única fuente de verdad").
- **`js/components/general-navbar.js`**: módulo ES que define el custom element `<general-navbar>`. Se encarga de cargar (`fetch`) el fragmento, inyectarlo en la página y **marcar automáticamente** el enlace activo según la vista actual (`index.html`, `member1.html`…`member5.html`, `bitacora.html`).

**Uso en cada HTML:**

```html
<general-navbar></general-navbar>
...
<script type="module" src="js/components/general-navbar.js"></script>
```

Si se modifica la navegación, solo hay que editar `components/navbar.html` y el cambio se replica en **las 7 vistas** automáticamente. Los dropdowns y el toggler de Bootstrap funcionan sobre el contenido inyectado gracias a la delegación de eventos de Bootstrap 5.3 (Light DOM).

---

- **Paleta Hexadecimal:**
  - Color Principal (Primary): #0d6efd (Bootstrap Primary)
  - Color Secundario (Secondary): #6c757d (Bootstrap Secondary)
  - Color de Fondo (Background): #f8f9fa (Light Gray)
  - Color de Texto (Text): #212529 (Dark Neutral)
- **Google Fonts:**
  - Fuente Principal: **System UI / Roboto (fallback) / apple-system / Segoe UI / Sans-Serif**
  - > **Nota técnica:** el sitio actualmente usa la pila de fuentes del sistema (sin descargar fuentes de Google) para máxima performance y consistencia con Bootstrap. Además, la etiqueta `<title>` y los textos de la portada están compuestos en la fuente tipográfica por defecto del sistema. Si se desea una fuente tipográfica de Google Fonts (ej. sin problema _Inter_ o _Poppins_), el equipo debe incorporar el `<link>` del CDN de Google Fonts en cada `<head>` y definir acá el `font-family` principal.
- **Iconografía:**
  - Bootstrap Icons (mediante CDN)

---

### Optimización SEO (Search Engine Optimization)

Se han implementado las siguientes mejoras para optimizar la visibilidad en motores de búsqueda:

- **Título de la Página (`<title>`):** Se ha actualizado el título en `index.html` para ser más descriptivo y relevante, incluyendo palabras clave importantes del proyecto.
- **Meta Descripción (`<meta name="description">`):** Se ha añadido una meta descripción concisa y atractiva en `index.html` que resume el contenido de la página, crucial para las SERPs (Páginas de Resultados del Motor de Búsqueda).
- **Meta Palabras Clave (`<meta name="keywords">`):** Se han incluido palabras clave relevantes en `index.html` para ayudar a los motores de búsqueda a entender el contexto del sitio (aunque su impacto directo en el ranking actual es menor, contribuye a la coherencia).
- **Jerarquía de Encabezados (H1, H2):** Se mantiene una estructura semántica clara con un `<h1>` para el título principal y `<h2>` para las secciones clave, lo que facilita la indexación del contenido.
- **Atributo `lang="es"`:** El idioma de la página está correctamente especificado como español, lo que ayuda a la segmentación geográfica en los resultados de búsqueda.

---

### Funciones JavaScript

Toda la interactividad está en [`js/main.js`](../js/main.js), cargado en la portada y en los 5 perfiles. Se detallan las funciones de la **portada** y de **cada perfil**, tal como pide la rúbrica.

#### Portada (`index.html`)

- **Botón "Saludar al equipo" (`welcomeAlertBtn`)**
  - **Explicación:** Al hacer clic en el botón principal de la portada, se muestra un `alert` de bienvenida que orienta al usuario sobre el contenido del sitio (perfiles y bitácora). Implementado con `document.getElementById('welcomeAlertBtn')` y un `addEventListener('click', ...)` dentro del `DOMContentLoaded`.
  - **Captura de Pantalla:** `![Portada - botón de saludo](img/capturas/portada-saludo.png)` _(pendiente de capturar; reemplazar por la imagen real en `img/capturas/`)_

#### Perfiles Individuales (`member1.html` … `member5.html`)

- **Desplegable "Ver detalles adicionales" (`toggleBioBtn` / `extraInfo`)**
  - **Explicación:** Cada tarjeta de perfil tiene un botón que alterna la visibilidad de información extra usando `classList.toggle('d-none')`. Además, cambia el texto del botón ("Ver/Ocultar detalles adicionales") y su clase Bootstrap (`btn-primary` ↔ `btn-outline-primary`) para reflejar el estado abierto/cerrado. Todo mediante manipulación del DOM.
  - **Captura de Pantalla:** `![Perfil - desplegable de biografía](img/capturas/perfil-desplegable.png)` ⬇️ (reemplazar por captura real en `img/capturas/`)

---

### URL Publicada en Vercel

- **Enlace al sitio publicado:** [`Mirá el proyecto en Vercel`](https://dswf-2-a-2-c26-desarrollo-de-sistem-beige.vercel.app/)

---

### Evolución del Proyecto

- **Fase 1 (Actual):** Creación del esqueleto base, maquetación responsiva con Bootstrap 5.3, estructuración de perfiles para 5 integrantes, y establecimiento de la bitácora y documentación en README.
- **Fases Posteriores:** Integración de contenidos reales del equipo, personalización de avatares/imágenes y ampliación de funcionalidades en los siguientes TPs.

---

### Uso de IA y Autoría

- **Herramientas y Modelos Utilizados:**
  - **Cline** (Agente de programación autónoma en VS Code) impulsado por el modelo **Gemini 3.5**.
- **Aportes en Código o Contenido:**
  - Asistencia en la estructuración general del proyecto, generación del código base de HTML (index.html, páginas de perfiles member1.html a member5.html, y biitacora.html), estilos CSS personalizados con soporte para breakpoints obligatorios (400px, 900px y 1200px), y lógica interactiva en JavaScript.
  - Redacción y estructuración completa de la documentación técnica y el presente README.md.
- **Plan Gratuito o Pago:**
  - Uso de herramientas de desarrollo integradas con API de Gemini 3.5.
- **Experiencia Previa del Equipo:**
  - El equipo utiliza asistentes de IA como soporte técnico y de estructuración para acelerar la configuración inicial, manteniendo siempre la revisión y validación manual de cada componente.
- **Avatares, Logos o Imágenes:**
  - Uso temporal de marcadores de posición (placeholders) listos para ser reemplazados por los avatares o fotos reales de los integrantes.
- **Revisión y Adaptación:**
  - Leandro revisó, probó y validó minuciosamente la estructura generada por el agente (Cline con Gemini 3.5), asegurando el cumplimiento total de los requisitos de Bootstrap 5.3, la responsividad y la rúbrica del TP1 antes de su publicación.

### Pendientes para la entrega (checklist de aprobación)

Para que el proyecto quede **aprobado**, el README debe cerrar estos puntos que dependen del equipo:

- [ ] **Capturas de pantalla reales** (`img/capturas/`): portada con el botón de saludo y perfil con el desplegable abierto/cerrado. Hoy figuran como placeholders.
- [ ] **Perfil de GitHub de cada integrante**: reemplazar los `USUARIO-...` de la sección _Integrantes_ por el link real de cada uno.
- [ ] (Opcional) Incorporar una **Google Font** real (CDN) si se quiere cumplir literalmente la guía de estilos, y documentarla acá.

---
