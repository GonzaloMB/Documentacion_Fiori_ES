<h1 align="center">DOCUMENTACIÓN FIORI 🖥️ </h1>

<div align="center">
 Repositorio de documentación Fiori, UI5, Fiori Elements, CDS.
</div>
<div align="center">
  <h3> 📝 
    <a href="https://www.linkedin.com/in/gonzalo-meana-balseiro-90a523188/">
      Contact Me
    </a>
  </h3>
    <h3> 💻  
    <a href="http://gonzalomb.com">
      Check my website
    </a>
  </h3>
</div>

# FIORI | UI5 | ABAP CDS | CAP CDS 📚
Documentación recolectadas durante mis años trabajando como programador UI5.

## Diferencias entre SAPUI5 y FIORI

UI5 y Fiori son dos tecnologías diferentes, pero que están estrechamente relacionadas en el ecosistema de SAP.

UI5 es una biblioteca de interfaz de usuario basada en JavaScript que se utiliza para desarrollar aplicaciones web para el entorno SAP. Esta biblioteca proporciona un conjunto de controles y componentes que se pueden utilizar para crear interfaces de usuario modernas y responsivas que se ejecutan en un navegador web. UI5 se utiliza principalmente para desarrollar aplicaciones que se ejecutan en la nube o en un servidor.

Por otro lado, Fiori es una plataforma de diseño y desarrollo de aplicaciones móviles y web para SAP. Fiori se basa en UI5, pero también incluye otros componentes como el servidor de aplicaciones SAP Gateway, que permite acceder a los datos de SAP, y el servidor de autenticación SAP Identity Management. Fiori proporciona un conjunto de plantillas y patrones de diseño que se pueden utilizar para crear aplicaciones móviles y web que sean consistentes con la marca y la experiencia de usuario de SAP.

Las principales diferencias entre UI5 y Fiori son:

* UI5 se utiliza para desarrollar aplicaciones web para el entorno SAP, mientras que Fiori se utiliza para diseñar y desarrollar aplicaciones móviles y web para SAP.

* UI5 es una biblioteca de interfaz de usuario basada en JavaScript, mientras que Fiori es una plataforma de diseño y desarrollo que incluye otros componentes además de UI5.

* UI5 proporciona un conjunto de controles y componentes para crear interfaces de usuario, mientras que Fiori proporciona patrones de diseño y plantillas para crear aplicaciones móviles y web.

* UI5 se ejecuta en un navegador web, mientras que Fiori puede ejecutarse en una variedad de plataformas, incluyendo navegadores web, dispositivos móviles y aplicaciones de escritorio.

En resumen, UI5 y Fiori son tecnologías diferentes pero complementarias. UI5 se utiliza para desarrollar aplicaciones web para el entorno SAP, mientras que Fiori se utiliza para diseñar y desarrollar aplicaciones móviles y web que sean consistentes con la marca y la experiencia de usuario de SAP. Ambas tecnologías son importantes en el ecosistema de SAP y se utilizan en conjunto para proporcionar una experiencia de usuario coherente y moderna en todas las plataformas.


## Operaciones CRUD oData
Las operaciones CRUD son un acrónimo que representa las cuatro operaciones básicas que se pueden realizar en una base de datos o en cualquier sistema que maneje datos. CRUD significa:

Create (Crear): se refiere a la operación de agregar un nuevo registro a la base de datos o sistema.
* Read (Leer): se refiere a la operación de obtener información de un registro específico o de una lista de registros en la base de datos o sistema.
* Update (Actualizar): se refiere a la operación de modificar un registro existente en la base de datos o sistema.
* Delete (Eliminar): se refiere a la operación de eliminar un registro existente en la base de datos o sistema.
Estas operaciones son esenciales para cualquier sistema que maneje datos y son ampliamente utilizadas en aplicaciones web, aplicaciones móviles, sistemas de gestión de bases de datos, entre otros.
Ejemplos de cómo realizar operaciones CRUD con oData utilizando SAPUI5:

### Crear un registro:
```javascript
var oEntry = {};
oEntry.Nombre = "John";
oEntry.Apellido = "Doe";
oEntry.Edad = 30;
oModel.create("/Usuarios", oEntry, {
    success: function(){
        console.log("Registro creado correctamente");
    },
    error: function(oError){
        console.log("Error al crear el registro: " + oError.message);
    }
});
```
Este código crea un nuevo registro en el entityset "Usuarios" utilizando la función create del modelo oData.

### Leer un registro:
```javascript
oModel.read("/Usuarios('12345')", {
    success: function(oData){
        console.log("Registro leído correctamente");
        console.log(oData);
    },
    error: function(oError){
        console.log("Error al leer el registro: " + oError.message);
    }
});
```
Este código lee el registro con la clave "12345" del entityset "Usuarios" utilizando la función read del modelo oData.

### Actualizar un registro:
```javascript
var oEntry = {};
oEntry.Nombre = "Jane";
oEntry.Apellido = "Doe";
oEntry.Edad = 35;
oModel.update("/Usuarios('12345')", oEntry, {
    success: function(){
        console.log("Registro actualizado correctamente");
    },
    error: function(oError){
        console.log("Error al actualizar el registro: " + oError.message);
    }
});
```
Este código actualiza el registro con la clave "12345" del entityset "Usuarios" utilizando la función update del modelo oData.

### Eliminar un registro:
```javascript
oModel.remove("/Usuarios('12345')", {
    success: function(){
        console.log("Registro eliminado correctamente");
    },
    error: function(oError){
        console.log("Error al eliminar el registro: " + oError.message);
    }
});
```
Este código elimina el registro con la clave "12345" del entityset "Usuarios" utilizando la función remove del modelo oData.

Estos son solo algunos ejemplos básicos de cómo realizar operaciones CRUD con oData utilizando SAPUI5. Por supuesto, la implementación real dependerá de la estructura del modelo y del entityset en particular.


## Operaciones con modelos
Ejemplos de algunas operaciones que se pueden realizar con modelos en SAPUI5:

### getProperty 
Esta operación se utiliza para obtener el valor de una propiedad específica de un modelo. Por ejemplo:
```javascript
var oModel = new sap.ui.model.json.JSONModel();
oModel.setData({
    name: "Juan",
    age: 30
});

var sName = oModel.getProperty("/name");
// sName tendrá el valor "Juan"
```
###  setProperty
Esta operación se utiliza para establecer un nuevo valor para una propiedad específica de un modelo. Por ejemplo:
```javascript
var oModel = new sap.ui.model.json.JSONModel();
oModel.setData({
    name: "Juan",
    age: 30
});

oModel.setProperty("/name", "Pedro");
// La propiedad "name" del modelo ahora tendrá el valor "Pedro"
```
### createEntry
Esta operación se utiliza para crear una nueva entrada en un modelo que está vinculado a una entidad de servicio OData. Por ejemplo:
```javascript
var oModel = new sap.ui.model.odata.v2.ODataModel("/odata/service");

oModel.createEntry("/EntitySet", {
    properties: {
        name: "Juan",
        age: 30
    }
});
// Se creará una nueva entrada en la entidad "EntitySet" del servicio OData
```
###  submitChanges
Esta operación se utiliza para enviar los cambios realizados en un modelo que está vinculado a una entidad de servicio OData al servidor. Por ejemplo:
```javascript
var oModel = new sap.ui.model.odata.v2.ODataModel("/odata/service");

oModel.setProperty("/EntitySet('id')/name", "Pedro");

oModel.submitChanges();
//Se envian Los cambios realizados en la propiedad "name" de la entrada con el ID "id" 
//de la entidad "EntitySet" del servicio OData al servidor
```
### refresh
Esta operación se utiliza para actualizar los datos de un modelo que está vinculado a una entidad de servicio OData. Por ejemplo:
```javascript
var oModel = new sap.ui.model.odata.v2.ODataModel("/odata/service");

oModel.refresh();
// Se actualizarán los datos del modelo desde el servidor
```
Estos son solo algunos ejemplos de las operaciones que se pueden realizar con modelos en SAPUI5. Existen muchas otras operaciones que pueden variar según el tipo de modelo y la entidad de servicio OData que se esté utilizando.
## Navegación entre vistas

La navegación entre vistas en SAPUI5 se refiere a la capacidad de cambiar dinámicamente entre diferentes vistas o pantallas en una aplicación web. En SAPUI5, se pueden crear diferentes vistas utilizando diferentes tecnologías como XML, JavaScript o JSON.
La navegación entre vistas en SAPUI5 se puede implementar utilizando enrutamiento (routing). En el enrutamiento, se utiliza una configuración de rutas (routes) y targets que mapean la URL de la aplicación a la vista correspondiente. Cuando se navega a una ruta en particular, el enrutador (router) carga la vista correspondiente y la muestra en la pantalla.
### Navegación sin parametros

Para navegar entre vistas en SAPUI5 con enrutamiento (routing) sin parámetros, puedes seguir los siguientes pasos:
En primer lugar, debes definir el enrutamiento en el archivo manifest.json de tu proyecto. Aquí es donde se define la ruta que se utilizará para navegar entre vistas. Por ejemplo:
```json
"routing": {
  "config": {
    "routerClass": "sap.m.routing.Router",
    "viewType": "XML",
    "viewPath": "myapp.view",
    "controlId": "app",
    "controlAggregation": "pages",
    "async": true,
    "routes": [
      {
        "name": "home",
        "pattern": "",
        "target": "home"
      },
      {
        "name": "about",
        "pattern": "about",
        "target": "about"
      }
    ],
    "targets": {
      "home": {
        "viewName": "Home",
        "viewLevel": 1,
        "viewId": "home"
      },
      "about": {
        "viewName": "About",
        "viewLevel": 1,
        "viewId": "about"
      }
    }
  }
}
```
En este ejemplo, se definen dos rutas, una para la vista "Home" y otra para la vista "About". La ruta "home" utiliza un patrón vacío, lo que significa que será la vista principal de la aplicación, mientras que la ruta "about" utiliza el patrón "about".

A continuación, debes crear las vistas correspondientes y sus controladores. En este ejemplo, se tienen las vistas "Home" y "About".

Finalmente, para navegar entre las vistas utilizando el enrutador, puedes utilizar la función navTo.

```javascript
var oRouter = sap.ui.core.UIComponent.getRouterFor(this);
oRouter.navTo("about");
```
En este ejemplo, se navega a la vista "About" utilizando el nombre de la ruta "about". También se puede navegar a la vista "Home" utilizando el nombre de la ruta "home". En ambos casos, el enrutador cargará la vista correspondiente y la mostrará en la pantalla.

### Navegación con parametros
Para navegar de una vista a otra en SAPUI5 con parámetros, puedes usar el enrutamiento o routing. El enrutamiento es un mecanismo que permite la navegación entre vistas y controladores en SAPUI5.

Para utilizar el enrutamiento con parámetros, debes seguir los siguientes pasos:

En primer lugar, debes definir el enrutamiento en el archivo manifest.json de tu proyecto. Aquí es donde se define la ruta que se utilizará para navegar entre vistas. Por ejemplo:
```json
"routing": {
  "config": {
    "routerClass": "sap.m.routing.Router",
    "viewType": "XML",
    "viewPath": "myapp.view",
    "controlId": "app",
    "controlAggregation": "pages",
    "async": true,
    "routes": [
      {
        "name": "detail",
        "pattern": "detail/{id}",
        "target": "detail"
      }
    ],
    "targets": {
      "detail": {
        "viewName": "Detail",
        "viewLevel": 2,
        "viewId": "detail",
        "viewData": {
          "myParam": "{id}"
        }
      }
    }
  }
}
```
En este ejemplo, se define una ruta llamada "detail" que utiliza el patrón "detail/{id}". El parámetro "id" se pasa como parte de la URL y se utilizará para mostrar datos específicos en la vista "Detail".

A continuación, debes crear la vista "Detail" y su controlador correspondiente. En el controlador, puedes obtener el parámetro "id" utilizando la función this.getOwnerComponent().getComponentData().myParam.

```javascript
sap.ui.define([
  "sap/ui/core/mvc/Controller"
], function(Controller) {
  "use strict";

  return Controller.extend("myapp.view.Detail", {

    onInit: function() {
      var id = this.getOwnerComponent().getComponentData().myParam;
      // utilizar el parámetro "id" para mostrar los datos correspondientes
    }

  });

});
```
Finalmente, para navegar a la vista "Detail" con el parámetro "id", puedes utilizar la función navTo del enrutador.
```javascript
var oRouter = sap.ui.core.UIComponent.getRouterFor(this);
oRouter.navTo("detail", {
  id: "1234"
});
```
En este ejemplo, se navega a la vista "Detail" con el parámetro "id" igual a "1234". Este valor se pasará como parte de la URL y se utilizará en el controlador de la vista "Detail" para mostrar los datos correspondientes.


⌨️ with ❤️ love [GonzaloMB](https://github.com/GonzaloMB) 😊

