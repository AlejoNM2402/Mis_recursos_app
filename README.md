# Mis Recursos - Aplicación de Gestión Personal

Este proyecto permite registrar y gestionar el progreso de recursos personales como libros, series y películas. Los datos se almacenan en una base de datos MongoDB.

---

## Estructura del Proyecto

- `recursos_50_documentos.json`: Archivo con por lo menor 50 documentos de ejemplo para la colección `recursos`.
- Este `README.md`: Guía completa de uso de la base de datos desde la terminal (`mongosh`).
- Para la creacion de la base de datos, la hice adentro de la coneccion con mi cluster de mongo atlas.

  ## CRUD en la base de datos con la mongosh:

### Crear:
Para la insercion de documentos y la creacion de los mismos en la coleccion de los recursos en la base de datos usé insertOne e insertMany, que se usan así:
insertOne:
insert one se usa para crear e insertar un documento dentro de la colección que se desea y se escribe db.el nombre de la coleccion que se va a usar.insertOne({los datos del documento que se desea insertar}), por ejemplo:

db.usuarios.insertOne({
  nombre: "Alejandro",
  edad: 30,
  email: "alejo@mail.com"
})

insertMany:
insertMany es como insertOne pero en vez de insertar un solo documento se pueden insertar mas, siendo separados con comas, por ejemplo:

db.usuarios.insertOne({
  nombre: "Alejandro",
  edad: 30,
  email: "alejo@yahoo.com"
},
{
  nombre: "Jose",
  edad: 12,
  email: "jose@mail.com"
}
)



### Leer:
Para leer y filtrar datos, se puede usar find, el cual se puede usar de bastantes maneras filtrando diferentes datos para obtener datos diferentes basados en la filtracion que se les haga, por ejemplo:

- Se puede usar find con la siguiente extructura: db.la coleccion en la que se quiere trabajar.find(filtro, proyeccion), por ejemplo puedes usar db.recursos.find para que se gte muestren todos los documentos que estan en la coleccion de recursus o puedes filtrarlos haciendo un db.recursos.find({nombre: "Juan"}), para que se te muestren todos los documentos que tienen como nombre Juan dentro de la coleccion de recursos.


### Actualizar:
Para editar la informacion que hay dentro de los documentos de la coleccion puedes usar updateOne o UpdateMany:

updateOne:
la extructura para esta consulta es: 
db.<colección>.updateOne(
  { <filtro de búsqueda> },
  { <operadores de actualización> },
  { <opciones> } // (opcional)
)

un ejemplo podria ser:

db.recursos.updateOne(
  { nombre: "1984" },
  { $set: { valoracion: 4, reseña: "Relectura interesante." } }
)

En este caso lo que hace es buscar el documento con el nombre 1984 dentro de la coleccion recursos y modificafr su valoracion y su reseña, en el caso de que haya mas documentos con este nombre, solo modifica el primero pues updateOne solo puede actualizar un documento a la vez.

updateMany:
la estructura de esta consulta es:
db.<colección>.updateMany(
  { <filtro> },
  { <operadores de actualización> }
)

un ejemplo puede ser:

db.recursos.updateMany(
  { estado: "en progreso" },
  { $set: { estado: "terminado" } }
)
 en este caso lo que se hace es modificar el estado de todos los docunentos que esten en un estado terminado dentro de la coleccion recursos.


 ### Eliminar:

 Para eliminar documentos desde la mongosh es sencillo, puedes usar deleteOne o deleteMany:

 deleteOne:
 para esta consulta tu extructura debe ser: db.<colección>.deleteOne(
  { <condición> }
)

por ejemplo:

db.recursos.deleteOne({ nombre: "1984" })
esta elimina solo el primer documento que se llame 1984 ya que deleteOne como su nombre lo dice solo puede eliminar un documento a la vez.

deleteMany:
su estructura es basicamente la misma, solo que cambias el deleteOne por el deleteMany y debes tener en cuenta que deleteMany como su nombre lo dice si puede eliminar varios documentos a la vez, por ejemplo:

db.recursos.deleteOne({ reseña: 2 })
en este caso esta consulta lo que hace es eliminar todos los documentos que tengan una reseña igual a 2 y que esten dentro de la coleccion recursos. 
 



