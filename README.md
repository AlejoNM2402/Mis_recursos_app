# 📚 Mis Recursos - Aplicación de Gestión Personal

Este proyecto permite registrar y gestionar el progreso de recursos personales como libros, series y películas. Los datos se almacenan en una base de datos MongoDB.

---

## 📁 Estructura del Proyecto

- `recursos_50_documentos.json`: Archivo con 50 documentos de ejemplo para la colección `recursos`.
- Este `README.md`: Guía completa de uso de la base de datos desde la terminal (`mongosh`).

---

## 🚀 Importar datos en MongoDB

### 📥 Desde la terminal:

```bash
mongoimport --uri "TU_URI_DE_CONEXIÓN" --collection recursos --file recursos_50_documentos.json --jsonArray

