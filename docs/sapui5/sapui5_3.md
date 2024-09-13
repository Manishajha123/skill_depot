### Bootstrapping
The process of loading and initializing SAPUI5 is called bootstrapping.

```HTML

<script
        id="sap-ui-bootstrap"
        src="resources/sap-ui-core.js"
        data-sap-ui-theme="sap_bluecrystal"
        data-sap-ui-resourceroots='{
            "engineerdigitalmaintenance": "./"
        }'
        data-sap-ui-oninit="module:sap/ui/core/ComponentSupport"
        data-sap-ui-compatVersion="edge"
        data-sap-ui-async="true"
        data-sap-ui-frameOptions="trusted"
    ></script>

```

**id :** "sap-ui-bootstrap" to ensure proper booting of the  SAPUI5 runtime.

**src :** it initializes the SAPUI5 runtime and loads additional resources.

**data-sap-ui-theme:** The SAPUI5 controls support different themes.

**data-sap-ui-compatVersion:** To make use of the most recent functionality of SAPUI5 we define the compatibility version as edge.

**data-sap-ui-resourceroots:** It defines the resource roots for the application namespaces. It maps the namespace "engineerdigitalmaintenance" to the root directory "./". This setup allows the application to load modules and resources correctly based on the defined namespaces.

**data-sap-ui-oninit:**  This attribute specifies a module that should be loaded once the SAPUI5 core has been initialized. The module "sap/ui/core/ComponentSupport" enables automatic instantiation of UI components that are defined in the HTML using the data-sap-ui-component attribute, allowing declarative use of SAPUI5 components.

**data-sap-ui-async:**
This enables asynchronous loading of SAPUI5 modules, improving the performance by loading resources in parallel and not blocking the page rendering. This is the recommended approach for better performance.

**data-sap-ui-frameOptions:**
This attribute specifies the frameOptions to control how the app can be embedded in an iframe. "trusted" allows embedding only from trusted sources, enhancing security by preventing clickjacking attacks.

### Flow of SAPUI5 App Execution & project structure?
* Index.html : loads ui5 libraries
* component.js: component configuration, router, and models are initialized
* manifest.json: configuration for the app
* controller: handles view logic
* view: defines the ui structure
* model: manage data

### Default Model

The default model refers to a data model that is set without a specific name, it to be usually a JSON model and can be accessed without explicitly naming.

```js

var oModel = sap.ui.getCore().getModel();  // Retrieves the default model

```

**Combobox setting binding values?  - "items"**

**Combobox as the default value?    - "selectedkey"**

**Add Secondary values to ComboBox? - "items"**

### Difference between sap.ui.table and sap.m.table?

**sap.ui.table.Table** 

 - Suitable for desktop-focused applications
 - Handle complex data interactions, large datasets, and advanced features.

**sap.m.Table**

 - Suitable for  mobile applications
 - Designed for lightweight use cases, focusing on responsiveness and adaptability across different screen sizes.


 **FORMATTERS**

- Formatters are JavaScript functions that take input data (e.g., from a model) and transform it into a desired output format suitable for display.

- They are often used in XML views to convert, format, or modify data values directly in the binding syntax, enhancing the presentation of data in the UI.

- Typical use cases include formatting dates, numbers, currency values, strings, or applying conditional formatting based on data values.

**Define a formatter function in a separate file**

```js

// formatter.js
sap.ui.define([], function () {
    "use strict";
    return {
        currencyFormatter: function (value) {
            return parseFloat(value).toFixed(2) + " USD";
        },
        dateFormatter: function (date) {
            if (!date) return "";
            var oDateFormat = sap.ui.core.format.DateFormat.getDateInstance({ pattern: "yyyy-MM-dd" });
            return oDateFormat.format(new Date(date));
        }
    };
});

```

**use formatter in XML:**

```xml

<mvc:View
    controllerName="myApp.controller.Main"
    xmlns:mvc="sap.ui.core.mvc"
    xmlns="sap.m">
    <Text text="{path: 'name', formatter: '.formatter.upperCaseFormatter'}" />  <!-- Applies the formatter -->
</mvc:View>

```


**Include the Formatter in the Controller: Load the formatter module in the controller using sap.ui.define.**

```js

// Main.controller.js
sap.ui.define([
    "sap/ui/core/mvc/Controller",
    "myApp/formatter/formatter"  // Adjust the path as needed
], function (Controller, formatter) {
    "use strict";
    return Controller.extend("myApp.controller.Main", {
        formatter: formatter,  // Assign formatter to the controller
        onInit: function () {
            // Initialization code
        }
    });
});


```

### Fragments

- Lightweight and Reusable UI

* Fragments can also be used directly within XML views

```xml

<mvc:View
    controllerName="myApp.controller.Main"
    xmlns:mvc="sap.ui.core.mvc"
    xmlns="sap.m"
    xmlns:core="sap.ui.core">
    <VBox>
        <!-- Load a fragment within a view -->
        <core:Fragment fragmentName="myApp.view.MyFragment" type="XML" />
    </VBox>
</mvc:View>

```

* We can create a seperate fragmemt file e.g., MyFragment.fragment.xml

```xml

<!-- MyFragment.fragment.xml -->
<core:FragmentDefinition xmlns="sap.m" xmlns:core="sap.ui.core">
    <Dialog id="myDialog" title="My Dialog" draggable="true" resizable="true">
        <content>
            <VBox>
                <Text text="This is a reusable dialog fragment." />
                <Input placeholder="Enter something..." />
            </VBox>
        </content>
        <beginButton>
            <Button text="OK" press="onDialogOkPress" />
        </beginButton>
        <endButton>
            <Button text="Cancel" press="onDialogCancelPress" />
        </endButton>
    </Dialog>
</core:FragmentDefinition>

```

* Fragments can be loaded into a view or controller using the sap.ui.xmlfragment function. This function loads the fragment and returns its content.

```js
// Main.controller.js
sap.ui.define([
    "sap/ui/core/mvc/Controller",
    "sap/ui/core/Fragment"
], function (Controller, Fragment) {
    "use strict";
    return Controller.extend("myApp.controller.Main", {
        onInit: function () {
            // Initialization logic
        },
        
        onOpenDialog: function () {
            var oView = this.getView();
            
            // Create or retrieve the fragment
            if (!this.byId("myDialog")) {
                // Load the fragment asynchronously
                Fragment.load({
                    id: oView.getId(),               // Assign the fragment ID
                    name: "myApp.view.MyFragment",  // Path to the fragment
                    controller: this               // Assign controller to handle events
                }).then(function (oDialog) {
                    // Connect the fragment's lifecycle to the view
                    oView.addDependent(oDialog);
                    oDialog.open();
                });
            } else {
                // Open the dialog if it already exists
                this.byId("myDialog").open();
            }
        },
        
        onDialogOkPress: function () {
            // Handle OK button press
            this.byId("myDialog").close();
        },
        
        onDialogCancelPress: function () {
            // Handle Cancel button press
            this.byId("myDialog").close();
        }
    });
});

```

### can one view have multiple controllers? - NO
### can one controller have multiple views? - yes

### Difference between sap.ui.define and sap.ui.require?

**sap.ui.define** is used to define a new module and declare its dependencies. It is primarily used for creating SAPUI5 modules, such as controllers, views, components, or utility functions.

 **sap.ui.require** is used to load one or more modules asynchronously at runtime. It does not define modules but rather fetches them as needed.

