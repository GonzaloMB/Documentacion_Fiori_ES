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


## "this.getView()" Vs. "sap.ui.getCore()"
En el contexto de una aplicación UI5, this.getView() y sap.ui.getCore() son dos funciones diferentes que se utilizan para acceder a objetos o componentes de la interfaz de usuario.

this.getView() es una función que se utiliza en un controlador de vista UI5 para obtener una referencia a la vista actual en la que se está trabajando. Esta función devuelve un objeto que representa la vista actual y que se puede utilizar para acceder a los controles y componentes de la vista. Por ejemplo, se puede utilizar this.getView().byId("myButton") para obtener una referencia al botón con el ID "myButton" en la vista actual.

Por otro lado, sap.ui.getCore() es una función que se utiliza para acceder a la instancia principal de la biblioteca UI5. Esta función devuelve un objeto que representa la instancia principal de la biblioteca UI5 y que se puede utilizar para acceder a los componentes principales de la biblioteca. Por ejemplo, se puede utilizar sap.ui.getCore().byId("myButton") para obtener una referencia al botón con el ID "myButton" en cualquier vista o componente de la aplicación.

Las principales diferencias entre this.getView() y sap.ui.getCore() son:

* this.getView() se utiliza para acceder a la vista actual en la que se está trabajando, mientras que sap.ui.getCore() se utiliza para acceder a la instancia principal de la biblioteca UI5.

* this.getView() devuelve un objeto que representa la vista actual y que se puede utilizar para acceder a los controles y componentes de la vista, mientras que sap.ui.getCore() devuelve un objeto que representa la instancia principal de la biblioteca UI5 y que se puede utilizar para acceder a los componentes principales de la biblioteca.

* this.getView() solo funciona en el contexto de un controlador de vista, mientras que sap.ui.getCore() se puede utilizar en cualquier parte de la aplicación UI5.

En resumen, this.getView() y sap.ui.getCore() son dos funciones diferentes que se utilizan para acceder a objetos o componentes de la interfaz de usuario en una aplicación UI5. this.getView() se utiliza para acceder a la vista actual en la que se está trabajando, mientras que sap.ui.getCore() se utiliza para acceder a la instancia principal de la biblioteca UI5 y a los componentes principales de la biblioteca.
## ¿Que son las "Expression Binding"?
Una "Expression Binding" es un enlace de datos en SAPUI5 que permite enlazar un valor de una propiedad de un control con una expresión que se evalúa dinámicamente en tiempo de ejecución. Esto permite que el valor de la propiedad se actualice automáticamente en respuesta a cambios en otras propiedades o modelos de datos.

La sintaxis para crear una expresión de enlace en SAPUI5 es la siguiente:

```xml
{= expression}
```
Donde "expression" puede ser cualquier expresión JavaScript válida. Por ejemplo, para enlazar el texto de un control Label con una propiedad "name" de un modelo de datos, se puede usar la siguiente expresión:

```xml
<Text text="{= ${myModel>/name} }" />
```
En este caso, el valor de la propiedad "text" del control Label se actualizará automáticamente cuando cambie la propiedad "name" del modelo de datos "myModel".

A continuación, te daré algunos ejemplos de Expression Binding con operadores ternarios, funciones y otras expresiones JavaScript en SAPUI5:

Usando el operador ternario para mostrar diferentes textos en función del valor de una propiedad:
```xml
<Text text="{= ${myModel>/age} >= 18 ? 'Eres mayor de edad' : 'Eres menor de edad' }" />
```
En este caso, el valor de la propiedad "text" del control Label mostrará diferentes textos en función de si el valor de la propiedad "age" del modelo de datos "myModel" es mayor o igual a 18.

Usando una función para convertir un valor de un modelo de datos en otro valor para mostrar en un control:
```xml
<Text text="{= myFunction(${myModel>/value}) }" />

function myFunction(value) {
  return value * 2;
}
```
En este caso, la función "myFunction" se define en el código JavaScript y se utiliza en la expresión de enlace de datos para convertir el valor de la propiedad "value" del modelo de datos "myModel" en otro valor que se mostrará en el control Label.

Usando expresiones JavaScript para concatenar diferentes valores de propiedades:
```xml
<Text text="{= 'Bienvenido, ' + ${myModel>/name} + ' ' + ${myModel>/surname} }" />
```
En este caso, la expresión de enlace de datos utiliza el operador "+" para concatenar diferentes valores de las propiedades "name" y "surname" del modelo de datos "myModel" y mostrarlos en el control Label..

En resumen, una "Expression Binding" en SAPUI5 es una forma poderosa y flexible de enlazar dinámicamente los valores de las propiedades de los controles con expresiones JavaScript que pueden evaluar y modificar datos en tiempo de ejecución.

## Diferencias entre instanciar un Model en la vista o en el core
En SAPUI5, un modelo de datos es una fuente de datos que se puede enlazar a los controles de la interfaz de usuario. Hay dos formas de instanciar un modelo de datos en SAPUI5: en la vista o en el core.

La principal diferencia entre instanciar un modelo de datos en la vista o en el core es que, al instanciarlo en el core, el modelo se puede compartir entre varias vistas y componentes. Esto puede ser útil en situaciones donde se necesita compartir datos entre diferentes partes de una aplicación.

A continuación, se presentan algunas de las diferencias más importantes entre instanciar un modelo en la vista o en el core:

* Instanciar un modelo en la vista significa que el modelo solo se puede utilizar en esa vista, mientras que instanciarlo en el core significa que se puede utilizar en toda la aplicación.

* Cuando se instancia un modelo en la vista, la vista es responsable de crear y gestionar el modelo. Cuando se instancia en el core, el modelo se crea y gestiona en un componente de nivel superior, que es responsable de compartir el modelo con otras partes de la aplicación.

* Al instanciar un modelo en la vista, es posible que se creen varias instancias del mismo modelo en diferentes vistas, lo que puede llevar a la duplicación de datos y al aumento del uso de memoria. Al instanciar en el core, se evita la duplicación de instancias de modelo y se reduce el uso de memoria.

* Si se instancia un modelo en el core, es posible que se deba pasar el modelo a las vistas a través de los parámetros de navegación. Esto puede hacer que el código sea más complejo y difícil de mantener.

En resumen, instanciar un modelo en la vista es más adecuado para aplicaciones pequeñas y simples, mientras que instanciar en el core es más adecuado para aplicaciones más grandes y complejas que requieren compartir datos entre diferentes partes de la aplicación

Instanciar un modelo en la vista:
```javascript
// En la vista
onInit: function() {
  // Crear un modelo JSON
  var oModel = new JSONModel({
    name: "John",
    surname: "Doe",
    age: 30
  });
  
  // Asignar el modelo a la vista
  this.getView().setModel(oModel);
}
```
En este ejemplo, se instancia un modelo JSON en la vista "onInit" utilizando el constructor "JSONModel" y se asigna a la vista utilizando el método "setModel" de la vista.

Instanciar un modelo en el core:
```javascript
// En el componente
init: function() {
  // Crear un modelo JSON
  var oModel = new JSONModel({
    name: "John",
    surname: "Doe",
    age: 30
  });
  
  // Asignar el modelo al componente
  this.setModel(oModel);
}
```
En este ejemplo, se instancia un modelo JSON en el componente "init" utilizando el constructor "JSONModel" y se asigna al componente utilizando el método "setModel" del componente.

Una vez que se ha instanciado el modelo en el componente, se puede acceder al modelo desde cualquier vista o control en la aplicación utilizando el método "getModel" de la vista o el control:

```javascript
// En una vista o control
var oModel = this.getModel();
```
Este método devuelve el modelo asignado al componente y lo hace accesible desde cualquier parte de la aplicación.


⌨️ with ❤️ love [GonzaloMB](https://github.com/GonzaloMB) 😊

