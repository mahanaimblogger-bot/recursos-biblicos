<p align="center">
  <img src="logo-mahanaim.jpg" alt="Mahanaim - Campamento de Dios" width="300" style="border-radius: 12px; border: 3px solid #d4ac0d;">
</p>

<p align="center">
  <h1>📖 Centro de Recursos Bíblicos</h1>
  <h3><em>Proyecto Mahanaim - "Campamento de Dios"</em></h3>
  
  [![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Activado-3C8DA0?style=for-the-badge&logo=github)](https://mahanaimblogger-bot.github.io/recursos-biblicos/)
  [![JSON](https://img.shields.io/badge/Formato-JSON-F7DF1E?style=for-the-badge&logo=json)]()
  [![HTML5](https://img.shields.io/badge/Tecnologia-HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)]()
</p>

---

## 📑 Tabla de Contenidos
1. [¿Qué es este proyecto?](#-qué-es-este-proyecto)
2. [Estructura del Repositorio](#-estructura-del-repositorio)
3. [Guía Paso a Paso](#-guía-paso-a-paso)
4. [Gestión de Iconos](#-gestión-de-iconos-y-tipos-de-recursos)
5. [Cheat Sheet de CSS](#-cheat-sheet-clases-css-para-el-contenido)
6. [Solución de Problemas](#-solución-de-problemas-comunes)
7. [Cómo deshacer cambios](#-cómo-deshacer-cambios-revertir)

---

## 🤔 ¿Qué es este proyecto?
Es una **Aplicación de Página Única (SPA)** creada en un solo archivo HTML (`recursos-biblicos.html`) que se conecta a archivos JSON para mostrar estudios bíblicos, sermones, videos y audios. No necesita base de datos ni lenguajes de programación del lado del servidor. Solo lee los archivos JSON alojados en GitHub Pages.

---

## 🗂️ Estructura del Repositorio
Tu repo **DEBE** mantener esta estructura exacta:

*   📄 `recursos-biblicos.html` ← La aplicación principal (NO renombrar)
*   📄 `index.json` ← Lista general de los 66 libros
*   📁 `data/`
    *   📄 `index.json` ← (Alternativa de ubicación para la lista general)
    *   📁 `genesis/` ← Carpeta del libro (usa el "slug")
        *   📄 `capitulos.json` ← Lista de capítulos de Génesis
        *   📄 `cap-1.json` ← Recursos del Capítulo 1
        *   📄 `cap-2.json` ← Recursos del Capítulo 2

> ⚠️ **REGLA DE ORO:** El nombre de la carpeta (`genesis`, `exodo`) debe coincidir exactamente con el campo `"slug"` en el `index.json`. El nombre de los archivos de capítulo debe ser siempre `cap-X.json`.

---

## 🛠️ Guía Paso a Paso

### 1. Agregar un capítulo nuevo a un libro existente
Supongamos que querés agregar el **Capítulo 4 de Génesis**.
*   **Paso A:** Creá el archivo `data/genesis/cap-4.json` con la estructura básica.
*   **Paso B:** Abrí `data/genesis/capitulos.json` y agregá el capítulo al array: 
    > `{"capitulo": "4", "total": 2, "tipos": ["estudio", "video"]}`
*   **Paso C:** Abrí `index.json` y sumá los recursos nuevos al `"total"` de Génesis.

### 2. Agregar un libro nuevo completo (Ej. Levítico)
*   **Paso A:** Creá la carpeta `data/levitico/`.
*   **Paso B:** Dentro de esa carpeta, creá el archivo `capitulos.json`.
*   **Paso C:** Creá los archivos `cap-1.json`, `cap-2.json`, etc., con sus recursos.
*   **Paso D:** En `index.json`, cambiá el `"total": 0` de Levítico por la cantidad de recursos totales que subiste.

### 3. Estructura de un recurso (Ejemplo de cap-4.json)
Cada recurso dentro del array `"recursos"` lleva estos campos:

*   **`tipo`**: Define el icono y cómo se muestra (ej: `"estudio"`, `"video"`, `"audio"`).
*   **`titulo`**: El nombre que aparece en la tarjeta (ej: `"La caída del hombre"`).
*   **`recurso_url`**: URL del video/audio/imagen. Va vacío `""` si es un estudio escrito.
*   **`contenido_html`**: El artículo/estudio en formato HTML.

**Comportamiento del campo `recurso_url` según el tipo:**

*   Si es **estudio**: Se ignora. Muestra el `contenido_html`.
*   Si es **video**: Va el **ID del video de YouTube** (ej: `dQw4w9WgXcQ`).
*   Si es **audio / sermon**: Va la **URL completa del archivo .mp3**.
*   Si es **imagen**: Va la **URL completa de la imagen .jpg/.png**.

---

## 🎨 Gestión de Iconos y Tipos de Recursos

Los iconos **NO** se configuran en los JSON, se configuran en el código JavaScript del HTML (`recursos-biblicos.html`). Buscá estas dos variables al principio del bloque `<script>`:

*   **Para AGREGAR un icono (Ej. Mapa):** Agregá la entrada en AMBOS objetos respetando la coma al final: `mapa:'🗺️'` en icons y `mapa:'Mapa Arqueológico'` en labels.
*   **Para ELIMINAR un icono:** Borralo de ambos objetos en el HTML.
*   **Para cambiar los iconos de un capítulo:** Editá el archivo `capitulos.json` de ese libro y cambiá el array `"tipos"` (ej: `["estudio", "video", "mapa"]`).

---

## 💡 Cheat Sheet: Clases CSS para el Contenido
Como el contenido se escribe en HTML dentro del JSON, usá estas clases de la app para que se vea bonito:

*   **Títulos:** Usá `class="titulo-entrada"` para el título principal y `class="subtitulo"` para los subtítulos.
*   **Versículos:** Usá `class="cita-versiculo"` (Caja dorada para versículos).
*   **Contexto:** Usá `class="caja-contexto"` (Caja azul para contexto histórico).
*   **Lingüística:** Usá `class="caja-linguistica"` (Caja marrón para palabras originales).
*   **Arqueología:** Usá `class="caja-arqueologica"` (Caja marrón claro).
*   **Profecía:** Usá `class="caja-profetica"` (Caja morada).
*   **Meditar:** Usá `class="caja-meditar"` (Caja dorada con emoji de oración).
*   **Impacto:** Usá `class="destacado-dramatico"` (Fondo azul oscuro con texto blanco) o `class="caja-fuego"` (Fondo rojo tipo fuego).
*   **Separador:** Usá `class="separador"` con un `✦ ✦ ✦` adentro.

> ⚠️ **IMPORTANTE PARA JSON:** Siempre escapá las comillas dobles dentro del `contenido_html` usando una barra invertida `\"` (por ejemplo: `<h2 class=\"subtitulo\">`).

---

## 🐛 Solución de Problemas Comunes

| Problema | Causa | Solución |
| :--- | :--- | :--- |
| Hice clic en un libro y da error | Falta el archivo `capitulos.json` o la carpeta tiene otro nombre. | Verificá que el `slug` en `index.json` coincida exactamente con el nombre de la carpeta en `data/`. |
| Agregué recursos pero no se ven | **Caché del navegador.** | Presioná `Ctrl + Shift + R` (o `Cmd + Shift + R` en Mac) para forzar la recarga. |
| Se ve bien en mi PC pero en el celular se desarma | Error de sintaxis en el JSON (una coma de más). | Pegá tu JSON en [jsonlint.com](https://jsonlint.com/) para verificar que no tenga errores. |
| El video de YouTube no se reproduce | Pusiste la URL completa en vez del ID. | En `recurso_url` solo va el ID (ej: `dQw4w9WgXcQ`), no `https://youtube.com/watch?v=...` |
| La tarjeta del capítulo no muestra los iconos nuevos | No actualizaste el array `tipos` en `capitulos.json`. | Agregá el tipo nuevo al array `["estudio", "video", "mapa"]`. |

---

## ⏪ Cómo deshacer cambios (Revertir)
Si editaste un JSON y lo rompiste, es muy fácil volver atrás:

1. Entrá al archivo en GitHub.
2. Hacé clic en el botón **"History"** (relojito 🕐).
3. Elegí la versión anterior (el commit verde que funcionaba).
4. A la derecha del archivo, clic en los **tres puntos (⋯)** → **"View file"**.
5. Clic en **"Raw"**, copiá todo el texto.
6. Volvé al archivo actual, clic en el **lápiz ✏️**, pegá el texto y hacé commit.

---

## 📌 Notas Finales
*   **Siempre actualiza los totales:** Cada vez que agregues un recurso, suma 1 al `"total"` en `capitulos.json` y también en `index.json`.
*   **Respaldos:** Antes de hacer cambios masivos en un JSON, conviene copiar su contenido en un bloc de notas por si algo sale mal.

<p align="center">
  <sub>Hecho con ❤️ para la comunidad de Mahanaim</sub>
</p>
