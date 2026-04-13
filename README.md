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

1. ¿Qué es este proyecto?
2. Estructura del Repositorio
3. Guía Paso a Paso
4. Estudios externos (HTML)
5. Anti-cache automático
6. Gestión de Iconos
7. Solución de Problemas

---

## 🤔 ¿Qué es este proyecto?

SPA en HTML que carga contenido desde JSON y archivos HTML externos en GitHub Pages.

✔ Sin backend  
✔ Sin base de datos  
✔ Sistema escalable  

---

## 🗂️ Estructura del Repositorio

recursos-biblicos.html  
data/  
  index.json  
  romanos/  
    capitulos.json  
    cap-7.json  
    cap-8.json  

estudios/  
  romanos/  
    romanos7.html  

---

## 🛠️ Guía Paso a Paso

### 1. Crear un estudio (HTML)

Ubicación:

estudios/romanos/romanos7.html

Ejemplo:

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

---

### 2. Crear el JSON del capítulo

Archivo:

data/romanos/cap-7.json

Ejemplo:

{
  "success": true,
  "data": {
    "recursos": [
      {
        "tipo": "estudio",
        "titulo": "El grito del prisionero",
        "archivo_html": "/estudios/romanos/romanos7.html"
      }
    ]
  }
}

---

### 3. Registrar el capítulo

Archivo:

data/romanos/capitulos.json

Ejemplo:

{
  "capitulo": "7",
  "total": 1,
  "tipos": ["estudio"]
}

---

## 🔥 Estudios externos (HTML)

### 💡 CLAVE

Los estudios NO van dentro del JSON.  
Se cargan desde la carpeta:

estudios/

---

### 📄 Regla de rutas

SIEMPRE usar:

/estudios/libro/archivo.html

Ejemplo:

/estudios/romanos/romanos7.html

---

### ⚠️ IMPORTANTE

✔ NO usar contenido_html  
✔ archivo_html es obligatorio para estudios  
✔ El HTML puede ser completo (head, style, etc.)  
✔ Debe existir físicamente en GitHub  

---

### 🚀 Ventajas

✔ Estudios largos sin errores  
✔ HTML limpio  
✔ Separación total entre datos y contenido  
✔ Escalable  

---

## 🚀 Anti-cache automático

El sistema usa:

?v=' + Date.now()

✔ Evita cache  
✔ Siempre carga lo último  
✔ No necesitas Ctrl + F5  

---

## 🎨 Gestión de Iconos

En el HTML principal:

var icons = {
  estudio:'📖',
  video:'🎬',
  audio:'🎧'
};

---

## 🐛 Solución de Problemas

No aparece capítulo → Revisar capitulos.json  
No carga estudio → Revisar ruta /estudios/...  
Funciona HTML directo pero no app → JSON mal configurado  
No se actualiza → GitHub tarda unos segundos  
Error JSON → Validar formato  

---

## 📌 Notas Finales

✔ JSON = índice  
✔ HTML = contenido real  
✔ Estudios van en /estudios/  
✔ No mezclar contenido_html con archivo_html  

---

🔥 Sistema profesional, limpio y listo para escalar
