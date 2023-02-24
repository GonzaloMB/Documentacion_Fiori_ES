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

# UI5 📚
Documentación recolectadas durante mis años trabajando como programador UI5.



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
// Se enviarán los cambios realizados en la propiedad "name" de la entrada con el ID "id" de la entidad "EntitySet" del servicio OData al servidor
```
### refresh
Esta operación se utiliza para actualizar los datos de un modelo que está vinculado a una entidad de servicio OData. Por ejemplo:
```javascript
var oModel = new sap.ui.model.odata.v2.ODataModel("/odata/service");

oModel.refresh();
// Se actualizarán los datos del modelo desde el servidor
```
Estos son solo algunos ejemplos de las operaciones que se pueden realizar con modelos en SAPUI5. Existen muchas otras operaciones que pueden variar según el tipo de modelo y la entidad de servicio OData que se esté utilizando.


# CAP CDS 

# FIORI ELEMENTS 

# ABAP CDS 



⌨️ with ❤️ love [GonzaloMB](https://github.com/GonzaloMB) 😊

