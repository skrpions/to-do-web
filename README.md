# ToDoWeb

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 15.2.1.

# Compartir app en red local

ng s --host=0.0.0.0 --port=4200 -o

luego debo ir a un buscador desde cualquier dispositivo y colocar la ip de la red: ej: 192.168.0.106:4200

---

## Estructura

core: services, models, pipes
data: archivos simuladores de base de datos
Routes - Modules: (Guest, Usuarios, Proveedores, ventas, compras)Rutas: Migas de pan
shared: Header, Footer, Sidebar, Angular-Material

## Importante: Asignar alias a las rutas

---

Ir a tsconfig.json y agregar lo siguiente:
"paths": {
"@core/_": [
"src/app/core/_"
],
"@data/_": [
"src/app/data/_"
],
"@modules/_": [
"src/app/modules/_"
],
"@shared/_": [
"src/app/shared/_"
],
}

---

## ---------------_ Routes _-------------------------

#Crear Módulo routes
ng g m routes --routing

---

## ---------------_ Guests _-------------------------

#Crear Módulo routes
ng g m routes/guest --routing

## Crear los nuevos Componentes dentro de la carpeta guest

ng g c routes/guest/pages/home
ng g c routes/guest/components/header
ng g c routes/guest/components/body
ng g c routes/guest/components/form
ng g c routes/guest/components/footer

ng g c routes/guest/pages/detail
ng g c routes/guest/pages/list
ng g c routes/guest/pages/add
ng g c routes/guest/pages/edit

## Modelos

ng g i core/models/guest
ng g i core/models/department

## Servicios

ng g s core/services/department
ng g s core/services/translate
ng g s core/services/contact

## Pipes

ng g pipe core/pipes/translate

---

#Instalar Font-awesome : Iconos
npm install font-awesome

#Instalar SweerAlert2
npm install sweetalert2

#Desplegar app en GitHub-pages
ng deploy --base-href=https://skrpions.github.io/sigma-web/

---

## ---------------_ ANGULAR IN MEMORY WEB API _--------------------

## Instalar

npm i angular-in-memory-web-api@014.0 -D

ng g s data/InMemGuest --skip-tests

---

## ---------------_ JSON SERVER _--------------------

## Instalar

npm i -g json-server

## Crear un restData.js con el json y algunos datos dummy.

module.exports = function () {
var data = {
guests: [
{
department: 'Amazonas',
city: 'Leticia',
name: 'NESTOR MARTINEZ',
email: 'sksmartinez@gmail.com'
},
{
department: 'Cesar',
city: 'Astrea',
name: 'FELIPE MARTINEZ',
email: 'pipemartinez@gmail.com'
}
]
}
return data;
};

## Ir al archivo de package.json y pegar un nuevo script

"server":"json-server --port 5000 --watch src/app/data/restData.js",

## Ejecutar npm run server // Esto levantará el backend de prueba en el puerto 5000,

## Presionar la letras S si lo pide

## Ir al navegador y pegar la ruta: localhost:5000

---

## ---------------_ Unit Testing With Jasmine _--------------------

## Ejecutar las pruebas

ng test

## Ver el coverage

ng test --code-coverage

## ---------------_ Unit Testing With Jest _--------------------

## Instalar jest- Unit Testing

npm i @briebug/jest-schematic

## Ejecutar las pruebas en modo watch

npm run test:watch

## Ver el coverage

npm run test:coverage

## salir de modo watch

presionar la tecla W

---

## ---------------_ Shared _--------------------

#Crear Módulo Shared
ng g m shared --flat --export | Este módulo no tendrá rutas
ng g m shared/angular-material --flat --export

## Componentes dentro del modulo Shared

ng g c shared/components/header --skip-tests
ng g c shared/components/body
ng g c shared/components/footer
ng g c shared/components/error-page
