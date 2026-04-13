Aquí tienes tu **README actualizado, corregido y optimizado** con TODO lo que acabas de implementar (incluyendo aclaración clave: ahora los estudios se cargan desde `data/`, no desde `estudios/`, y cómo funciona realmente el sistema):

---

```md
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
4. [🔥 Estudios externos (HTML)](#-estudios-externos-html)
5. [🚀 Anti-cache automático](#-anti-cache-automático)
6. [Gestión de Iconos](#-gestión-de-iconos)
7. [Solución de Problemas](#-solución-de-problemas)

---

## 🤔 ¿Qué es este proyecto?

Es una **SPA (Single Page Application)** en HTML que carga contenido dinámicamente desde archivos JSON y HTML alojados en GitHub Pages.

✔ Sin backend  
✔ Sin base de datos  
✔ Todo funciona con JSON + HTML  

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

````

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
````

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

## 🔥 Estudios externos (HTML)

### 💡 CLAVE DEL SISTEMA

👉 **Ahora los estudios NO van dentro del JSON**
👉 Se cargan desde archivos `.html` externos

---

### 📄 Dónde van los estudios

SIEMPRE dentro de:

```
data/[libro]/
```

Ejemplo:

```
data/romanos/romanos7.html
```

---

### 📌 Ejemplo de estudio

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Romanos 7</title>
</head>
<body>

<h1>Romanos 7</h1>
<p>Contenido aquí...</p>

</body>
</html>
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

### ⚠️ REGLAS IMPORTANTES

✔ La ruta debe empezar con `/data/...`
✔ El archivo debe existir en GitHub
✔ NO usar `contenido_html` si usas `archivo_html`
✔ El HTML puede ser COMPLETO (con `<html>`, `<head>`, `<style>`, etc.)

---

### 🚀 Ventajas

✔ Estudios largos sin romper JSON
✔ HTML limpio y editable
✔ Escalable
✔ Más profesional

---

## 🚀 Anti-cache automático

El sistema incluye esto:

```javascript
?v=' + Date.now()
```

### 🔥 ¿Qué significa?

✔ Fuerza al navegador a cargar la versión más nueva
✔ Evita errores de caché
✔ No necesitas Ctrl + F5

---

## 🎨 Gestión de Iconos

Se configuran en el HTML principal:

```javascript
var icons = {
  estudio:'📖',
  video:'🎬',
  audio:'🎧'
};
```

---

## 🐛 Solución de Problemas

| Problema                  | Causa                | Solución                            |
| ------------------------- | -------------------- | ----------------------------------- |
| No aparece capítulo       | `capitulos.json` mal | Revisar estructura                  |
| No carga estudio          | Ruta incorrecta      | Verificar `/data/...`               |
| Abre HTML pero no en app  | JSON mal conectado   | Revisar `archivo_html`              |
| Cambios no se ven         | Caché                | Ya está solucionado automáticamente |
| Funciona uno pero otro no | Error en JSON        | Validar en jsonlint                 |

---

## 📌 Notas Finales

✔ JSON = índice
✔ HTML = contenido real
✔ Mantén todo dentro de `/data/`
✔ No mezclar `contenido_html` con `archivo_html`

---

<p align="center">
  <sub>🔥 Sistema limpio, escalable y listo para crecer</sub>
</p>
```
