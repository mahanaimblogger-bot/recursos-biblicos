Mahanaim
📖 Centro de Recursos Bíblicos
Proyecto Mahanaim - "Campamento de Dios"
GitHub Pages JSON HTML5

📑 Tabla de Contenidos
¿Qué es este proyecto?
Estructura del Repositorio
¿Cómo funciona la navegación?
Guía Paso a Paso: Agregar Contenido
Gestión de Iconos y Tipos de Recursos
Cheat Sheet: Clases CSS para el Contenido
Solución de Problemas Comunes
Cómo deshacer cambios (Revertir)
🤔 ¿Qué es este proyecto?
Es una Aplicación de Página Única (SPA) creada en un solo archivo HTML (recursos-biblicos.html) que se conecta a archivos JSON para mostrar estudios bíblicos, sermones, videos y audios.

No necesita base de datos ni lenguajes de programación del lado del servidor. Solo lee los archivos JSON alojados en este repositorio de GitHub Pages.

🗂️ Estructura del Repositorio
Tu repositorio DEBE mantener esta estructura exacta para que la app funcione:

recursos-biblicos/├── recursos-biblicos.html      ← La aplicación principal (NO renombrar)├── index.json                  ← Lista general de los 66 libros├── data/│   ├── index.json              ← (Alternativa de ubicación para la lista general)│   ├── genesis/                ← Carpeta del libro (usa el "slug")│   │   ├── capitulos.json      ← Lista de capítulos de Génesis│   │   ├── cap-1.json          ← Recursos del Capítulo 1│   │   ├── cap-2.json          ← Recursos del Capítulo 2│   │   └── cap-3.json          ← Recursos del Capítulo 3│   ├── exodo/                  ← Carpeta de Éxodo│   │   ├── capitulos.json│   │   └── cap-1.json│   └── romanos/                ← Carpeta de Romanos│       └── ...
⚠️ REGLA DE ORO: El nombre de la carpeta (genesis, exodo) debe coincidir exactamente con el campo "slug" en el index.json. El nombre de los archivos de capítulo debe ser siempre cap-X.json (donde X es el número del capítulo).

⚙️ ¿Cómo funciona la navegación?
El flujo de lectura de la app es el siguiente:

index.json: La app lee este archivo para armar la grilla de Libros (Génesis, Éxodo, etc.).
capitulos.json: Cuando el usuario hace clic en un libro, la app busca data/{slug}/capitulos.json para mostrar la lista de capítulos y sus iconos.
cap-X.json: Cuando el usuario hace clic en un capítulo, la app busca data/{slug}/cap-X.json para mostrar las tarjetas de recursos (Estudio, Video, Audio).
contenido_html: Al hacer clic en un recurso, la app inyecta el HTML que esté dentro de ese campo JSON directamente en la pantalla.
🛠️ Guía Paso a Paso: Agregar Contenido
1. Agregar un capítulo nuevo a un libro existente
Supongamos que querés agregar el Capítulo 4 de Génesis.

Paso A: Creá el archivo data/genesis/cap-4.json con la estructura básica (ver sección de abajo).
Paso B: Abrí data/genesis/capitulos.json y agregá el capítulo al array:
json

{"capitulo": "4", "total": 2, "tipos": ["estudio", "video"]}
Paso C: Abrí index.json y sumá los recursos nuevos al "total" de Génesis.
2. Agregar un libro nuevo completo (Ej. Levítico)
Paso A: Creá la carpeta data/levitico/.
Paso B: Dentro de esa carpeta, creá el archivo capitulos.json.
Paso C: Creá los archivos cap-1.json, cap-2.json, etc., con sus recursos.
Paso D: En index.json, cambiá el "total": 0 de Levítico por la cantidad de recursos totales que subiste.
3. Estructura de un recurso (Ejemplo de cap-4.json)
Cada recurso dentro del array "recursos" lleva estos campos:

Campo
¿Para qué sirve?
Ejemplo
tipo	Define el icono y cómo se muestra	"estudio", "video", "audio"
titulo	El nombre que aparece en la tarjeta	"La caída del hombre"
recurso_url	URL del video/audio/imagen (Vacio si es estudio)	"https://..." o "dQw4w9WgXcQ" (ID YT)
contenido_html	El artículo/estudio en formato HTML	"<h1>Titulo</h1><p>Texto...</p>"

Comportamiento del campo recurso_url según el tipo:

Si es estudio: Se ignora. Muestra el contenido_html.
Si es video: Va el ID del video de YouTube (ej: dQw4w9WgXcQ).
Si es audio / sermon: Va la URL completa del archivo .mp3.
Si es imagen: Va la **URL completa de la imagen .jpg/.png`.
🎨 Gestión de Iconos y Tipos de Recursos
Los iconos NO se configuran en los JSON, se configuran en el código JavaScript del HTML (recursos-biblicos.html).

Buscá estas dos variables al principio del bloque <script>:

javascript

var icons={estudio:'📖',sermon:'🛐',video:'🎬',audio:'🎧',imagen:'🖼️',diapositiva:'📊',pdf:'📄'};
var labels={estudio:'Estudio Bíblico',sermon:'Sermón / Predica',video:'Video Resumen',audio:'Audio / Podcast',imagen:'Imágenes / Mapas',diapositiva:'Diapositivas',pdf:'PDF / Documento'};
➕ Para AGREGAR un nuevo icono (Ej. Mapa):
Agregá la entrada en AMBOS objetos respetando la coma al final:

javascript

var icons={ ..., mapa:'🗺️' };
var labels={ ..., mapa:'Mapa Arqueológico' };
Una vez hecho esto, ya podés usar "tipo": "mapa" en tus archivos JSON.

❌ Para ELIMINAR un icono:
Borralo de ambos objetos en el HTML.
(Ojo: Si lo borras del HTML pero lo dejás en un JSON, se mostrará el ícono genérico 📄).

🔄 Cómo cambiar los iconos que se ven en un capítulo:
Editá el archivo capitulos.json de ese libro. El campo "tipos" controla qué etiquetas se muestran debajo de cada capítulo:

json

{"capitulo": "1", "total": 4, "tipos": ["estudio", "video", "sermon", "audio"]}
Cambiá ese array para mostrar solo los que quieras.

🎨 Cheat Sheet: Clases CSS para el Contenido
Como el contenido se escribe en formato HTML dentro del JSON, tenés que usar estas clases específicas de la app para que el texto se vea bonito. ¡Guárdalas de referencia!

Títulos y Textos:

<h1 class="titulo-entrada">Título Principal</h1>
<h2 class="subtitulo">Subtítulo</h2>
Usá <div class="contenedor-blog"> para envolver párrafos largos (<p>, <ul>, <ol>).
Cajas Especiales (¡Usalas, se ven increíbles!):

<div class="cita-versiculo"><h3>Génesis 1:1</h3><p>"En el principio..."</p></div> (Caja dorada para versículos)
<div class="caja-contexto"><h3>📌 Contexto Histórico</h3><p>Texto...</p></div> (Caja azul)
<div class="caja-linguistica"><h4>🔬 Análisis Lingüístico</h4><span class="palabra-original">בָּרָא</span><p>Texto...</p></div> (Caja marrón para palabras originales)
<div class="caja-arqueologica"><h4>🏛️ Arqueología</h4><p>Texto...</p></div> (Caja marrón claro)
<div class="caja-profetica"><h4>🔮 Profecía</h4><p>Texto...</p></div> (Caja morada)
<div class="caja-meditar"><h3>Reflexión</h3><p>Texto...</p></div> (Caja dorada con emoji de oración)
Destacados y Multimedia:

<div class="destacado-dramatico">"Frase con fuerte impacto"</div> (Fondo azul oscuro con texto blanco grande)
<div class="caja-fuego"><strong>Título de Fuego</strong><p>"Cita de impacto"</p></div> (Fondo rojo oscuro tipo fuego)
<div class="separador">✦ ✦ ✦</div> (Separador decorativo centrado)
🐛 Solución de Problemas Comunes
Problema
Causa
Solución
Hice clic en un libro y da error o no carga	Falta el archivo capitulos.json o la carpeta tiene otro nombre.	Verificá que el slug en index.json coincida exactamente con el nombre de la carpeta en data/.
Agregué recursos pero no se ven en la página	Caché del navegador. GitHub guardó la versión vieja.	Presioná Ctrl + Shift + R (o Cmd + Shift + R en Mac) para forzar la recarga.
Se ve bien en mi PC pero en el celular se desarma	Error de sintaxis en el JSON (una coma de más).	Pegá tu JSON en jsonlint.com para verificar que no tenga errores.
El video de YouTube no se reproduce	Pusiste la URL completa en vez del ID.	En recurso_url solo va el ID (ej: dQw4w9WgXcQ), no https://youtube.com/watch?v=...
La tarjeta del capítulo no muestra los iconos nuevos	No actualizaste el array tipos en capitulos.json.	Agregá el tipo nuevo al array ["estudio", "video", "mapa"].

⏪ Cómo deshacer cambios (Revertir)
Si editaste un JSON y lo rompiste, es muy fácil volver atrás:

Entrá al archivo en GitHub.
Hacé clic en el botón "History" (relojito 🕐).
Elegí la versión anterior (el commit verde que funcionaba).
A la derecha del archivo, clic en los tres puntos (⋯) → "View file".
Clic en "Raw", copiá todo el texto.
Volvé al archivo actual, clic en el lápiz ✏️, pegá el texto y hacé commit.
📌 Notas Finales
Siempre actualiza los totales: Cada vez que agregues un recurso, suma 1 al "total" en capitulos.json y también en index.json. Si los números no coinciden, no rompe la app, pero muestra información incorrecta al usuario.
Respaldos: Antes de hacer cambios masivos en un JSON, conviene copiar su contenido en un bloc de notas por si algo sale mal.
HTML en JSON: Recuerda escapar las comillas dobles dentro del contenido_html usando una barra invertida \" (por ejemplo: <h2 class=\"subtitulo\">).

Hecho con ❤️ para la comunidad de Mahanaim

```
