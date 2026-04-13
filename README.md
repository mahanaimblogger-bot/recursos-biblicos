<p align="center">
  <img src="logo-mahanaim.jpg" alt="Mahanaim - Campamento de Dios" width="300" style="border-radius: 12px; border: 3px solid #d4ac0d;">
</p>

<p align="center">
  <h1>📖 Centro de Recursos Bíblicos</h1>
  <h3><em>Proyecto Mahanaim - "Campamento de Dios"</em></h3>

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Activado-3C8DA0?style=for-the-badge\&logo=github)](https://mahanaimblogger-bot.github.io/recursos-biblicos/)
[![JSON](https://img.shields.io/badge/Formato-JSON-F7DF1E?style=for-the-badge\&logo=json)]()
[![HTML5](https://img.shields.io/badge/Tecnologia-HTML5-E34F26?style=for-the-badge\&logo=html5\&logoColor=white)]()

</p>

---

## 📑 Tabla de Contenidos

1. [¿Qué es este proyecto?](#-qué-es-este-proyecto)
2. [Estructura del Repositorio](#-estructura-del-repositorio)
3. [Guía Paso a Paso](#-guía-paso-a-paso)
4. [🔥 NUEVO: Estudios externos (HTML)](#-nuevo-estudios-externos-html)
5. [🚀 Anti-cache automático](#-anti-cache-automático)
6. [Gestión de Iconos](#-gestión-de-iconos-y-tipos-de-recursos)
7. [Cheat Sheet de CSS](#-cheat-sheet-clases-css-para-el-contenido)
8. [Solución de Problemas](#-solución-de-problemas-comunes)

---

## 🤔 ¿Qué es este proyecto?

SPA en HTML + JSON que carga estudios bíblicos desde GitHub sin backend.

---

## 🗂️ Estructura del Repositorio

```
recursos-biblicos.html
data/
  index.json
  romanos/
    capitulos.json
    cap-7.json
    cap-8.json
    romanos7.html
```

---

## 🛠️ Guía Paso a Paso

### 1. Crear un capítulo

Archivo:

```
data/romanos/cap-7.json
```

Ejemplo:

```json
{
  "success": true,
  "data": {
    "recursos": [
      {
        "tipo": "estudio",
        "titulo": "El grito del prisionero",
        "archivo_html": "/data/romanos/romanos7.html"
      }
    ]
  }
}
```

---

### 2. Registrar el capítulo

En:

```
data/romanos/capitulos.json
```

```json
{
  "capitulo": "7",
  "total": 1,
  "tipos": ["estudio"]
}
```

---

## 🔥 NUEVO: Estudios externos (HTML)

### 💡 ¿Qué es esto?

Ahora puedes escribir estudios COMPLETOS en archivos `.html`
en vez de meter todo dentro del JSON.

---

### 📄 Ejemplo

Archivo:

```
data/romanos/romanos7.html
```

```html
<h1>Romanos 7</h1>
<p>Esto es una prueba</p>
```

---

### 🔗 Cómo conectarlo

En el JSON:

```json
{
  "tipo": "estudio",
  "titulo": "Romanos 7",
  "archivo_html": "/data/romanos/romanos7.html"
}
```

---

### ⚠️ IMPORTANTE

* NO uses `contenido_html` si usas `archivo_html`
* La ruta debe empezar con `/data/...`
* Debe existir el archivo en GitHub

---

### 🚀 Ventajas

* Puedes hacer estudios largos sin romper JSON
* Puedes usar HTML completo limpio
* Más fácil de editar

---

## 🚀 Anti-cache automático

Se implementó esto en el código:

```javascript
url = base+'/data/... ?v=' + Date.now();
```

### 🔥 ¿Qué hace?

* Evita que el navegador use datos viejos
* GitHub actualiza al instante
* No necesitas Ctrl + F5

---

## 🎨 Gestión de Iconos

Se configuran en el HTML:

```javascript
var icons = {
  estudio:'📖',
  video:'🎬'
};
```

---

## 💡 Cheat Sheet CSS

Clases útiles:

* `titulo-entrada`
* `subtitulo`
* `cita-versiculo`
* `caja-contexto`
* `caja-linguistica`
* `caja-profetica`
* `caja-meditar`
* `destacado-dramatico`

---

## 🐛 Solución de Problemas

| Problema                             | Causa               | Solución                   |
| ------------------------------------ | ------------------- | -------------------------- |
| No aparece capítulo                  | JSON no actualizado | Espera o revisa estructura |
| No carga estudio                     | Ruta incorrecta     | Verifica `archivo_html`    |
| Funciona HTML directo pero no en app | Falta `/data/...`   | Corregir ruta              |
| No se ven cambios                    | Cache               | Ya está solucionado        |

---

## 📌 Notas Finales

✔ Usa `archivo_html` para estudios largos
✔ Usa JSON solo como índice
✔ Mantén estructura limpia

---

<p align="center">
  <sub>🔥 Sistema optimizado y listo para escalar</sub>
</p>
