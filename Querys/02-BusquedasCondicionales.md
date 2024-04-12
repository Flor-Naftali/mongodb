# Busquedas condicionales
# Operadores de comparación
| Operador | Descripción |
| -- | -- |
| $eq | igual |
| $gt | mayor que |
| $gte | mayor o igual |
| $in | buscar un elemento en un array |
| $lt | menor que |
| $lte | menor o igual |
| $ne | todos los elementos que no sean iguales |
| $nin | ninguno de los valores del array |
_ Selecciona todos los documentos de una colección
```m
db.Libros.find()
db.Libros.find({})
```
_ Seleccionar todos los documentos de la colección libros donde la
editorial sea biblio
```m
db.libros.find({editorial: 'Biblio'})
```
_Seleccionar todos los documentos de la coleccion libros donde el
precio sea igual a 25_
```m
db.libros.find({precio: 25})
```
## Busquedas con operadores logicos
**Sintaxis**
```
{<columna>:
<operador>:<valor>}, ...
```
_Seleccionar todos aquellos documentos de la coleccion libros donde el
precio sea mayor a 25_
```m
db.libros.find({precio: {$gt:25}})
```
_Seleccionar aquellos documentos de la coleccion libros donde el precio
sean mayores o iguales a 20_
```m
db.libros.find({precio:{$gte: 20}})
```
_Seleccionar aquellos documentos donde la editorial sea Biblio o
Planeta_
```
db.libros.find({editorial: {$in: ['Biblio', 'Planeta']}})
```
# Recuperar una sola fila

_Seleccionar todos aquellos docuemntos que sean biblio o planeta, pero
mostrando solamenente el primer documento encontrado_
```
db.libros.findOne({editorial: {$in: ['Biblio', 'Planeta']}})
```
```
db.libros.findOne({})
```