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

## UI5 🚀
Creation of UI5 application that consists of a creation form and a table where we will show the records created at the moment, the back-end part is made up of CDS and Odata Service

### Pre-requirements 📋
Ejemplos de cómo realizar operaciones CRUD con oData utilizando SAPUI5:

	1. Crear un registro:
javascript
Copy code
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
Este código crea un nuevo registro en el entityset "Usuarios" utilizando la función create del modelo oData.

	2. Leer un registro:
javascript
Copy code
oModel.read("/Usuarios('12345')", {
    success: function(oData){
        console.log("Registro leído correctamente");
        console.log(oData);
    },
    error: function(oError){
        console.log("Error al leer el registro: " + oError.message);
    }
});
Este código lee el registro con la clave "12345" del entityset "Usuarios" utilizando la función read del modelo oData.

Actualizar un registro:
```javascript
Copy code
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

Eliminar un registro:
javascript
Copy code
oModel.remove("/Usuarios('12345')", {
    success: function(){
        console.log("Registro eliminado correctamente");
    },
    error: function(oError){
        console.log("Error al eliminar el registro: " + oError.message);
    }
});
Este código elimina el registro con la clave "12345" del entityset "Usuarios" utilizando la función remove del modelo oData.

Estos son solo algunos ejemplos básicos de cómo realizar operaciones CRUD con oData utilizando SAPUI5. Por supuesto, la implementación real dependerá de la estructura del modelo y del entityset en particular.
![image](https://user-images.githubusercontent.com/55688528/221181155-ae044645-59cc-4b37-b838-5f24e1e450db.png)



## CAP CDS ⚙️

## FIORI ELEMENTS ⚙️

## ABAP CDS ⚙️



⌨️ with ❤️ love [GonzaloMB](https://github.com/GonzaloMB) 😊

