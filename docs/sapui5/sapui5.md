### SAPUI5
SAPUI5 is a framework for developing platform-independent, responsive applications according to the HTML5 standard with JavaScript and CSS3.

### SAPUI5 Architecture
SAPUI5 allows users to consume data from any service. It uses the model-view-controller (MVC) development concept, which consists of a three-part application: models, which contain data; views, which represent the data and the UI; and controllers, which handle the data and user interaction.

### Models
Models are containers for data and hold all the business data an application will work with. There are a handful of pre-defined model classes available in SAPUI5, including JSON and resource models.

### Views
Views are the front-end display of data by an application. Because this is the portion of the app that end-users work with, it’s important to incorporate design thinking and UI best practices when developing views.

### Controllers
Controllers implements the logic that bridges Models and Views.

### Lifecycle Methods or Lifecycle Hooks in SAPUI5 Controller
SAPUI5 provides predefined lifecycle methods for controller. These are also called controller lifecycle hooks. These methods are

- onInit()

- onBeforeRendering()

- onAfterRendering()

- onExit()

### onInit()
This method is called upon initialization of the View. The controller can perform its internal setup in this hook. It is only called once per View instance, unlike the onBeforeRendering and onAfterRendering hooks.

If you need to modify the view before it is displayed, for example bind data to view, initialize model; it can be done inside onInit() methd.

 
### onBeforeRendering()
This method is called every time the View is rendered, before the Renderer is called and the HTML is placed in the DOM-Tree. BOLD_It can be used to perform clean-up-tasks before re-rendering._BOLD

 
### onAfterRendering()
This method is called every time the View is rendered, after the HTML is placed in the DOM-Tree. It can be used to apply additional changes to the DOM after the Renderer has finished.

It can be used to do post-rendering manipulations of the HTML.

 
### onExit()
This method is called upon destruction of the View. The controller should perform its internal destruction in this hook. It is only called once per View instance, unlike the onBeforeRendering and onAfterRendering hooks.

