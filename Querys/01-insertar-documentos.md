# Primeros comandos en mongoDB
### Mostrar las bases de datos
`show dbs;`
`show databases;`
### Crear una base de datos
*En mongoDB para crear una base de datos debe contener por lo menos una
colleccion*
`use nombredelabasededatos`
*Ejemplo:*
`use db3;`
### Crear una collecion
`db.createColleccion("nombredelacollecion")`
*Ejemplo*
`db.createCollection("Alumnos")`
### Mostrar las collecciones de la BD
*Ejemplo:*
`show collections;`
# Introduccion a MongoDB
## Ejemplo de sintaxis de un json
`
{nombre: "Luis", edad: 45,
tel:7777}
`
## Ejemplo de sintaxis de json mas complejo
`
{
nombre: "Luisa",
edad: 42,
tel: 65544,
aficciones: [
"Ejercicio",
"Programar",
"Correr"
],
skills: {
"Programación": "20%",
"Diseño web": "45%"
}
}


# insertar documentos

---

_inserta un solo documento_

---m

db.Alumnos. insertOne(
    {
        nombre:"Maximiliano"
    });

--m
_insercion de Documento con Id Personalizado_

db.libros.insertMany([{
_id: 1,
titulo: 'El aleph',
autor: 'Borges',
editorial: 'Planeta',
precio: 20,
cantidad: 50
}
,
{
_id: 2,
titulo: 'Martin Fierro',
autor: 'Jose Hernandez',
editorial: 'Siglo XXI',
precio: 50,
cantidad: 12
}
,
{
_id: 3,
titulo: 'Aprenda PHP',
autor: 'Mario Molina',
editorial: 'Siglo XXI',
precio: 50,
cantidad: 20
}
,
{
_id: 4,
titulo: 'Java en 10 minutos',
editorial: 'Siglo XXI',
precio: 45,
cantidad: 1
}
,{
_id: 5,
titulo: 'Python para torpes',
editorial: 'Planeta',
precio: 25,
cantidad: 14
}
,
{
_id: 6,
titulo: 'Don quijote',
editorial: 'Biblio',
precio: 25,
cantidad: 14
}
,
{
_id: 7,
titulo: 'MongoDB para expertos',
editorial: 'Biblio',
precio: 34,
cantidad: 29
}
,
{
_id: 8,
titulo: 'MongoDB para novatos',
editorial: 'Biblio',
precio: 15,
cantidad: 12
}
,
{
_id: 9 ,
titulo: 'JSON para todos',
editorial: 'Planeta',
precio: 25,
cantidad: 15
}
]
)

### Formas de insertado de datos 

db2> db.create
db.createUser                 db.createCollection           db.createEncryptedCollection  db.createView
db.createRole

db2> db.create
db.createUser                 db.createCollection           db.createEncryptedCollection  db.createView
db.createRole

db2> db.createCollection("Alumnos")
{ ok: 1 }
db2> show dbs
admin    40.00 KiB
config   72.00 KiB
db1     196.00 KiB
db2       8.00 KiB
local    88.00 KiB
test     40.00 KiB
db2> use local
switched to db local
local> use db2
switched to db db2
db2> show collections
Alumnos
db2> db.Alumnos.insertOne(
... {
... nombre: "Diego Armando",
... apellidos: "Hernandez Lopez",
... sexo: "H",
... activo: true
... })
{
  acknowledged: true,
  insertedId: ObjectId('65f4e6633637e1348e6cb334')
}
db2> db.Alumnos.find({})
[
  {
    _id: ObjectId('65f4e6633637e1348e6cb334'),
    nombre: 'Diego Armando',
    apellidos: 'Hernandez Lopez',
    sexo: 'H',
    activo: true
  }
]
db2> db.createCollection("Paises")
{ ok: 1 }
db2> db.Paises.find()

db2> db.Ciudades.insertOne(
... {
... ciudad:"Madrid"
... })
{
  acknowledged: true,
  insertedId: ObjectId('65f4e7233637e1348e6cb335')
}
db2> show collections
Alumnos
Ciudades
Paises
db2> db.Alumnos.find()
[
  {
    _id: ObjectId('65f4e6633637e1348e6cb334'),
    nombre: 'Diego Armando',
    apellidos: 'Hernandez Lopez',
    sexo: 'H',
    activo: true
  }
]
db2> db.Alumnos.insertOne(
... {
... nombre: "Roberto",
... apellidos:"Cabeza de Vaca",
... edad: 34,
... aficiones: ["Programación", "Base de Datos", "Redes", "Ganado"]
... })
{
  acknowledged: true,
  insertedId: ObjectId('65f4e7f93637e1348e6cb336')
}
db2> db.Alumnos.insertOne(
... {
... nombre: "Soyla",
... apellidos: "Vaca del Corral",
... edad:23,
... cv:{
... informatica:"Bueno",
... marketing:"Excelente",
... programacion: "Bajo"
... }
... })
{
  acknowledged: true,
  insertedId: ObjectId('65f4e8d13637e1348e6cb337')
}
db2> db.Alumnos.find()
[
  {
    _id: ObjectId('65f4e6633637e1348e6cb334'),
    nombre: 'Diego Armando',
    apellidos: 'Hernandez Lopez',
    sexo: 'H',
    activo: true
  },
  {
    _id: ObjectId('65f4e7f93637e1348e6cb336'),
    nombre: 'Roberto',
    apellidos: 'Cabeza de Vaca',
    edad: 34,
    aficiones: [ 'Programación', 'Base de Datos', 'Redes', 'Ganado' ]
  },
  {
    _id: ObjectId('65f4e8d13637e1348e6cb337'),
    nombre: 'Soyla',
    apellidos: 'Vaca del Corral',
    edad: 23,
    cv: {
      informatica: 'Bueno',
      marketing: 'Excelente',
      programacion: 'Bajo'
    }
  }
]
db2> db.Alumnos.insertMany(
... [
... {
...    nombre:"Daniel",
...    edad:20,
...    carrera: "Ing. en Entornos Virtuales"
... },
... {
...    nombre: "Flor",
...    apellidos: "Silvestre",
...    comunidad: "Santa Maria Macua",
...    pasatiempos: [ "Lavar", "Bicicleta", "Chelear"],
...    habilidades: {
...                   RealidadVirtual: "80%",
...                   SQL: "45%",
...                   Marketing: "99.9%"
...                 }
... }
... ]
... )
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('65f4ea9c3637e1348e6cb338'),
    '1': ObjectId('65f4ea9c3637e1348e6cb339')
  }
}
