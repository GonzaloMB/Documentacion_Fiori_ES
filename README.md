<h1 align="center">DOCUMENTACIÓN Fiori 🖥️ </h1>

<div align="center">
 Repositorio de Docu
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

## Starting 🚀
Creation of UI5 application that consists of a creation form and a table where we will show the records created at the moment, the back-end part is made up of CDS and Odata Service

### Pre-requirements 📋

_Tools you need to be able to develop this application_

* **SAP Logon** 
* **Eclipse**
* **SAP Web IDE** or **SAP BAS** 

## Practical case ⚙️

_In this application we are going to develop both the back-end and the front-end part_

### Back-end 🔩
#### 1. ABAP CDS
* **TRANSACTIONAL:** From this view we will consume the table created previously in SAP Logon
```abap
@AbapCatalog.sqlViewName: 'ZTFORMULARIO'
@AbapCatalog.compiler.compareFilter: true
@AbapCatalog.preserveKey: true
@AccessControl.authorizationCheck: #CHECK
@EndUserText.label: 'CDS Formulario Transaccional'
@VDM.viewType: #TRANSACTIONAL
define view ZT_FORMULARIO as select from zformulario_ui5 {
    key nombre,
    key apellido,
    key dni,
    movil,
    direccion
}

```
* **CONSUMITION:** From this view we will consume and activate both the oData and the BOPF, being able to also give annotations for visualization from the front-end 
```abap
@AbapCatalog.sqlViewName: 'ZCFORMULARIO'
@AbapCatalog.compiler.compareFilter: true
@AbapCatalog.preserveKey: true
@AccessControl.authorizationCheck: #CHECK
@EndUserText.label: 'CDS Formulario Consumicion'
@VDM.viewType: #CONSUMPTION
@ObjectModel.writeEnabled: true
@ObjectModel.writeActivePersistence: 'zformulario_ui5'
@ObjectModel.semanticKey: [ 'nombre' ] 
@ObjectModel: {
    transactionalProcessingEnabled: true,
    compositionRoot: true,
    createEnabled: true,
    updateEnabled: true,
    deleteEnabled: true
}
@OData: {
    publish: true
}
define view ZC_FORMULARIO as select from ZT_FORMULARIO {
    @UI: {
      lineItem: [ { position: 10, label: 'Name' } ]}
    @EndUserText.label: 'Name' 
    key nombre,
    @UI: {
     lineItem: [ { position: 20, label: 'Surname' } ] }
    @EndUserText.label: 'Surname' 
    key apellido,
    @UI: {
     lineItem: [ { position: 30, label: 'ID' } ] }
    @EndUserText.label: 'ID' 
    key dni,
    @UI: {
      lineItem: [ { position: 40, label: 'TMobile Phone' } ] }
    @EndUserText.label: 'Mobile Phone' 
    movil,
    @UI: {
      lineItem: [ { position: 50, label: 'Email' } ]}
    @EndUserText.label: 'Email' 
    direccion    
}
```

### Front-End ⌨️
#### 2. UI5 Fiori elements applications (Web IDE)
* Select SAPUI5 Application as the template.

![image](https://user-images.githubusercontent.com/55688528/182622309-19fec7f8-5676-4596-b2c9-cea501563b69.png)

* Fill the project name, title, namespace and description.

* Configure the the OData service on the manifest.json.
```json
		"dataSources": {
			"ZC_FORMULARIO_CDS": {
				"uri": "/sap/opu/odata/sap/ZC_FORMULARIO_CDS/",
				"type": "OData",
				"settings": {
					"localUri": "localService/metadata.xml",
					"annotations": [
						"annotation0"
					]
				}
			},
			"annotation0": {
				"type": "ODataAnnotation",
				"uri": "annotations/annotation0.xml",
				"settings": {
					"localUri": "annotations/annotation0.xml"
				}
			}
		}
  
  ```
* Next I will show the main view where we will paint the form and the table.

```xml
<mvc:View controllerName="ZFORMULARIO_UI5.ZFORMULARIO_UI5.controller.View1" xmlns:mvc="sap.ui.core.mvc" xmlns:l="sap.ui.layout"
	xmlns:f="sap.ui.layout.form" xmlns:core="sap.ui.core" xmlns="sap.m" xmlns:smartFilterBar="sap.ui.comp.smartfilterbar"
	xmlns:smartTable="sap.ui.comp.smarttable" xmlns:html="http://www.w3.org/1999/xhtml"
	xmlns:app="http://schemas.sap.com/sapui5/extension/sap.ui.core.CustomData/1" xmlns:tnt="sap.tnt">
	<tnt:ToolHeader id="toolHeader">
		<core:Icon src="sap-icon://sap-ui5" id="iconHeader"/>
		<Text text="UI5 FORM" id="textHeader"/>
	</tnt:ToolHeader>
	<VBox class="sapUiSmallMargin">
		<f:Form id="FormToolbar" editable="true" ariaLabelledBy="Title1">
			<f:toolbar>
				<Toolbar id="TB1">
					<core:Icon src="sap-icon://form" id="iconForm"/>
					<Title id="Title1" text="User Creation"/>
					<ToolbarSpacer/>
					<Button id="btnCrear" text="Save" icon="sap-icon://add" press="onCrear"/>
				</Toolbar>
			</f:toolbar>
			<f:layout>
				<f:ResponsiveGridLayout labelSpanXL="4" labelSpanL="3" labelSpanM="4" labelSpanS="12" adjustLabelSpan="false" emptySpanXL="0" emptySpanL="4"
					emptySpanM="0" emptySpanS="0" columnsXL="2" columnsL="1" columnsM="1" singleContainerFullSize="false"/>
			</f:layout>
			<f:formContainers>
				<f:FormContainer ariaLabelledBy="Title2" id="personalInformationBox">
					<f:toolbar >
						<Toolbar id="personalInformationToolbar">
							<Title id="Title2" text="Personal Information"/>
						</Toolbar>
					</f:toolbar>
					<f:formElements>
						<f:FormElement label="Name">
							<f:fields >
								<Input id="Nombre" required="true" placeholder="Enter Name"/>
							</f:fields>
						</f:FormElement>
						<f:FormElement label="Surname">
							<f:fields>
								<Input id="Apellido" required="true" placeholder="Enter Surname"/>
							</f:fields>
						</f:FormElement>
						<f:FormElement label="ID">
							<f:fields>
								<Input id="DNI" required="true" placeholder="Enter ID"/>
							</f:fields>
						</f:FormElement>
					</f:formElements>
				</f:FormContainer>
				<f:FormContainer ariaLabelledBy="Title3" id="contactDetailsBox">
					<f:toolbar>
						<Toolbar id="contactDetailsToolbar">
							<Title id="Title3" text="Contact Details"/>
						</Toolbar>
					</f:toolbar>
					<f:formElements>
						<f:FormElement label="Mobile Phone">
							<f:fields>
								<Input id="Movil" type="Number"  placeholder="Enter Mobile Phone"/>
							</f:fields>
						</f:FormElement>
						<f:FormElement label="Email">
							<f:fields>
								<Input id="Mail" type="Email"  placeholder="Enter Email"/>
							</f:fields>
						</f:FormElement>
					</f:formElements>
				</f:FormContainer>
			</f:formContainers>
		</f:Form>
	</VBox>
	<VBox fitContainer="true">
		<smartTable:SmartTable id="LineItemsSmartTable" entitySet="ZC_FORMULARIO" tableType="Table" demandPopin="true" useExportToExcel="true"
			beforeExport="onBeforeExport" useVariantManagement="true" useTablePersonalisation="true" header="Users" showRowCount="true"
			persistencyKey="SmartTableAnalytical_Explored" enableAutoBinding="true" class="sapUiResponsiveContentPadding">
			<smartTable:customToolbar id="customToolbar">
				<OverflowToolbar design="Transparent" id="OverflowToolbar">
					<ToolbarSpacer/>
					<OverflowToolbarButton icon="sap-icon://delete" tooltip="Delete Record" press="eliminarRegistro"/>
				</OverflowToolbar>
			</smartTable:customToolbar>
		</smartTable:SmartTable>
	</VBox>
</mvc:View>
```
* This is the respective controller where we do several validations and perform the create and delete for the different records

```javascript
sap.ui.define([
	"sap/ui/core/mvc/Controller",
	"sap/m/MessageBox",
	"sap/m/MessageToast"
], function (Controller, MessageBox, MessageToast) {
	"use strict";
	return Controller.extend("ZFORMULARIO_UI5.ZFORMULARIO_UI5.controller.View1", {
		//Create Function
		onCrear: function () {
			//Save model into var
			var oModel = this.getOwnerComponent().getModel();
			var that = this;
			//Save mail value and character to check mail
			var email = this.getView().byId("Mail").getValue();
			var mailregex = /^\w+[\w-+\.]*\@\w+([-\.]\w+)*\.[a-zA-Z]{2,}$/;
			//Save values required fields 
			var nombreField = this.getView().byId("Nombre").getValue();
			var apellidoField = this.getView().byId("Apellido").getValue();
			var dniField = this.getView().byId("DNI").getValue();
			//Validations
			if (!mailregex.test(email) && email !== "") {
				MessageBox.error(email + " is not a valid email address");
				document.getElementById("container-ZFORMULARIO_UI5---View1--Mail-content").style.backgroundColor = '#ff6c6c';
				document.getElementById("container-ZFORMULARIO_UI5---View1--Mail-inner").style.color = "white";
			} else if (nombreField === "" || apellidoField === "" ||
				dniField === "") {
				MessageBox.error("Fill in the required fields");
				if (nombreField === "") {
					document.getElementById("container-ZFORMULARIO_UI5---View1--Nombre-content").style.backgroundColor = '#ff6c6c';
					document.getElementById("container-ZFORMULARIO_UI5---View1--Nombre-inner").style.color = "white";
				}
				if (apellidoField === "") {
					document.getElementById("container-ZFORMULARIO_UI5---View1--Apellido-content").style.backgroundColor = '#ff6c6c';
					document.getElementById("container-ZFORMULARIO_UI5---View1--Apellido-inner").style.color = "white";
				}
				if (dniField === "") {
					document.getElementById("container-ZFORMULARIO_UI5---View1--DNI-content").style.backgroundColor = '#ff6c6c';
					document.getElementById("container-ZFORMULARIO_UI5---View1--DNI-inner").style.color = "white";
				}
			} else if (oModel.aBindings[0].aKeys.toString().includes(nombreField) && oModel.aBindings[0].aKeys.toString().includes(
					apellidoField) && oModel.aBindings[0].aKeys.toString().includes(dniField)) {
				MessageBox.error("The record is duplicate");
				document.getElementById("container-ZFORMULARIO_UI5---View1--Nombre-content").style.backgroundColor = '#ff6c6c';
				document.getElementById("container-ZFORMULARIO_UI5---View1--Nombre-inner").style.color = "white";
				document.getElementById("container-ZFORMULARIO_UI5---View1--Apellido-content").style.backgroundColor = '#ff6c6c';
				document.getElementById("container-ZFORMULARIO_UI5---View1--Apellido-inner").style.color = "white";
				document.getElementById("container-ZFORMULARIO_UI5---View1--DNI-content").style.backgroundColor = '#ff6c6c';
				document.getElementById("container-ZFORMULARIO_UI5---View1--DNI-inner").style.color = "white";
			} else {
				//Create array with the new form register
				var oEntry = {
					"nombre": that.getView().byId("Nombre").getValue(),
					"apellido": that.getView().byId("Apellido").getValue(),
					"dni": that.getView().byId("DNI").getValue(),
					"movil": that.getView().byId("Movil").getValue(),
					"direccion": that.getView().byId("Mail").getValue()
				};
				//Push the new register into the table
				oModel.create("/ZC_FORMULARIO", oEntry, {
					success: function (oData) {
						//After create the new register clean the form and set the correct css colors
						that.getView().byId("Nombre").setValue("");
						that.getView().byId("Apellido").setValue("");
						that.getView().byId("DNI").setValue("");
						that.getView().byId("Movil").setValue("");
						that.getView().byId("Mail").setValue("");
						document.getElementById("container-ZFORMULARIO_UI5---View1--Mail-content").style.backgroundColor = '#c3c6d5';
						document.getElementById("container-ZFORMULARIO_UI5---View1--Mail-inner").style.color = '#22223b';
						document.getElementById("container-ZFORMULARIO_UI5---View1--Nombre-content").style.backgroundColor = '#c3c6d5';
						document.getElementById("container-ZFORMULARIO_UI5---View1--Nombre-inner").style.color = "22223b";
						document.getElementById("container-ZFORMULARIO_UI5---View1--Apellido-content").style.backgroundColor = '#c3c6d5';
						document.getElementById("container-ZFORMULARIO_UI5---View1--Apellido-inner").style.color = "22223b";
						document.getElementById("container-ZFORMULARIO_UI5---View1--DNI-content").style.backgroundColor = '#c3c6d5';
						document.getElementById("container-ZFORMULARIO_UI5---View1--DNI-inner").style.color = "22223b";
						//Show message Success
						var msgSuccess = "Record created";
						MessageToast.show(msgSuccess);
					},
					error: function (oData) {
						//Show message Error
						var msgError = "Error creating record";
						MessageToast.show(msgError);
					}
				});
			}
		},
		//Delete Function
		eliminarRegistro: function () {
			//Save model into var
			var oModel = this.getOwnerComponent().getModel();
			var that = this;
			//Array with the selected register
			var indiceDelete = that.getView().byId("container-ZFORMULARIO_UI5---View1--LineItemsSmartTable-ui5table")._oLegacySelectionPlugin.oSelectionModel
				.aSelectedIndices;
			//Loop when is selected more then one register
			for (let n of indiceDelete) {
				//Create Path of the register to delete
				var sPath = "/" + oModel.aBindings[0].aKeys[n];
				//Delete from table
				oModel.remove(sPath, {
					success: function (oData) {
						//Show message Success
						var msgSuccess = "Record deleted";
						MessageToast.show(msgSuccess);
					},
					error: function (oData) {
						//Show message Error
						var msgError = "Error deleting record";
						MessageToast.show(msgError);
					}
				});
			}
		}
	});
});
```
* Finally this is the CSS made for this form
```css
body {
    background-color: #f2e9e4;
}

.sapMLabel .sapMLabelColonAndRequired {
    display: none;
}

div#container-ZFORMULARIO_UI5---View1--toolHeader {
    background-color: #4a4e69;
    display: flex;
    border: none;
}

div#container-ZFORMULARIO_UI5---View1--TB1 {
    border: none;
    background: #c3c6d5;
    color: #22223b;
    border-radius: 8rem;
    box-shadow: 3px 3px 3px rgb(0 0 0 / 15%);
}

span#container-ZFORMULARIO_UI5---View1--btnCrear-inner {
    cursor: pointer;
    border: none;
    background: #ffb685;
    border-radius: 8rem;
    color: #fff;
}

span#container-ZFORMULARIO_UI5---View1--btnCrear-inner:hover {
    background: #fff;
    color: #ffb685;
}

span#container-ZFORMULARIO_UI5---View1--btnCrear-img {
    color: #fff;
}

span#container-ZFORMULARIO_UI5---View1--btnCrear-img:hover {
    color: #ffb685;
}

span#container-ZFORMULARIO_UI5---View1--Title1-inner {
    font-size: 20px;
}

span#container-ZFORMULARIO_UI5---View1--iconForm {
    font-size: 20px;
}

span#container-ZFORMULARIO_UI5---View1--iconHeader {
    font-size: 30px;
    color: #ffb685;
}

span#container-ZFORMULARIO_UI5---View1--textHeader {
    font-size: 20px;
    color: #ffb685;
}

div#container-ZFORMULARIO_UI5---View1--personalInformationBox---Panel {
    border-radius: 1rem;
    background: #fef3eb;
    box-shadow: 5px 8px 5px rgb(0 0 0 / 20%);
}

div#container-ZFORMULARIO_UI5---View1--FormToolbar--Grid-wrapperfor-container-ZFORMULARIO_UI5---View1--contactDetailsBox---Panel {
    border-radius: 1rem;
    background: #fef3eb;
    box-shadow: 5px 8px 5px rgb(0 0 0 / 20%);
}

div#container-ZFORMULARIO_UI5---View1--Nombre-content {
    border: none;
    background: #c3c6d5;
    color: #22223b;
    border-radius: 8rem;
}

div#container-ZFORMULARIO_UI5---View1--Apellido-content {
    border: none;
    background: #c3c6d5;
    color: #22223b;
    border-radius: 8rem;
}

div#container-ZFORMULARIO_UI5---View1--DNI-content {
    border: none;
    background: #c3c6d5;
    color: #22223b;
    border-radius: 8rem;
}

div#container-ZFORMULARIO_UI5---View1--Movil-content {
    border: none;
    background: #c3c6d5;
    color: #22223b;
    border-radius: 8rem;
}

div#container-ZFORMULARIO_UI5---View1--Mail-content {
    border: none;
    background: #c3c6d5;
    color: #22223b;
    border-radius: 8rem;
}

div#container-ZFORMULARIO_UI5---View1--personalInformationToolbar {
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    background-color: #4a4e69;
}

div#container-ZFORMULARIO_UI5---View1--contactDetailsToolbar {
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    background-color: #4a4e69;
}

span#container-ZFORMULARIO_UI5---View1--Title2-inner {
    color: white;
}

span#container-ZFORMULARIO_UI5---View1--Title3-inner {
    color: white;
}

div#container-ZFORMULARIO_UI5---View1--OverflowToolbar {
    border: none;
    background: #ffb685;
    color: #fff;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    box-shadow: 5px 8px 5px rgb(0 0 0 / 20%);
}

span#container-ZFORMULARIO_UI5---View1--LineItemsSmartTable-header-inner {
    color: white;
}

div#container-ZFORMULARIO_UI5---View1--LineItemsSmartTable-ui5table {
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    box-shadow: 5px 8px 5px rgb(0 0 0 / 20%);
}

.sapUiTableSelectAllCheckBox::after,
.sapUiTableRowSelectionCell::after {
    background-color: #ffb685 !important;
    color: #fff !important;
}

.sapMMessageToast {
    box-sizing: unset;
    border: none;
    background: #ffb685;
    color: #fff;
    border-radius: 8rem;
    font-size: 16px;
    font-family: "Poppins", sans-serif;
}

bdi#__element0-label-bdi:before {
    content: "*" !important;
    color: red !important;
    font-weight: bold !important;
}

bdi#__element1-label-bdi:before {
    content: "*" !important;
    color: red !important;
    font-weight: bold !important;
}

bdi#__element2-label-bdi:before {
    content: "*" !important;
    color: red !important;
    font-weight: bold !important;
}
```
## Testing the UI5 Form 👨‍💻

https://user-images.githubusercontent.com/55688528/182627079-1004c56e-835a-4a38-9eee-d6e43dde2e23.mp4

## Acknowledgement 📚
- **ABAP CDS**
- **CSS**
- **Annotations**
- **UI5**

## Built with 🛠️
_Back-end:_
* **ABAP CDS**

_Gateway:_
* **oData**

_Front-End:_
* **UI5**
* **CSS**
* **Annotations**

---

⌨️ with ❤️ love [GonzaloMB](https://github.com/GonzaloMB) 😊

