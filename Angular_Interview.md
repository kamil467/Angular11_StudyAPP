------------------------------------------------------------Basics----------------------------------
1. What is component ?
ANS: components are basic building blocks for Angular applications.
--------------------------
###### 2. What is Module ?
ANS: Angular application must have atleast one Module, it is following module based development.
Modules are logical boundary of angular app. each module can have multiple components , directives , services etc.
--------------------------------------------------------------------------------
###### 3. What is boostrapping in Angualr ?
This loading AppModule and root component for starting the angular application knows as boostrap.
main.ts files - we can define which module should be AppModule or root modules.
index file - we mention App module's boostrap component.
Boostrap component section will be required only in root module not in feature modules.
BrowserModule - the services registered in this modules are singleton scope hence this module should be included only in root module not in feature modules.
-----------------------------------------------------------------------------
###### 4.What is directives ?
This is an angular concepts which extends behvaior of HTML.
basically components itself a directive.
There are 3 type of diretives 
1.Components.
2. Attributes - [ngModel], [formGroup],[formControlName],[routerLink] 
3. Structural: *ngIf, *ngFor, *ngSwitch
--------------------------------------------------------------------------
###### 5. What are the type of bindins available in Angualr ?
1. property binding
 - property binding : ( [property]="data")  component to view
   
2. string interoplation ( component -> view)
3. event binding (view -> component)
4. ngModel - two way binding (view/component -> component/view)
--------------------------------------------------------------------
6. What are the types of FORMS in Angular application ?
1. Template driven : validation, template ref , bindings happen at HTML.
2. ReactiveForms/Model Driven : Angular form object created in component, validations, bindings implemented in component level.
-------------------------------------------------------------------------------------------
7. What are Angular Validation classes ?
-ng-touched: control tocuhed
-ng-untouched : control not touched yet.
-ng-pristine: value not modified. (it can be touched or untouched)
-ng-dirty: value modified.(it happens when control touched )
-ng-valid/invalid : will switch based on value.
-----------------------------------------------------
8. What is template ref# in Angualr ? 
It is used to store angular object ref .
example : 
<form ngForm #myForm ="ngForm" > 
--------------------------------------------
9. How do you access template elements in component ?
using ViewChild decorator.
----------------------------------------------------
10. How do you protect routes in Angular ?
Implementing AuthGuard service. There is an interface CanActivate helps to protect the routes. 
We need to create custom service which should implement this interface.
--------------------------------------------------------------------------
11. How do you unsubscribe an observable ?
It is a two step process.
1-> create a component level variable to hold the subscribtion.
2-> assign subscribe outcome to this variable.
3 -> use Ondestroy hooks to unsubcribe the subcription.
-------------------------------------------------------------------------
12. What is pipe in Angular ?
It is an Angular concept which used in component template to transform the data.
----------------------------------------------------------------------------
13. What is Async Pipe ?
It internally subscribes to observable and returns latest value that observable is emitted.
When component destroyed , the async pipe automatically unsubscribe the observable inorder to avoid memory leaks.
-------------------------------------------------------------------------------------
14. What are the various ways that once can make service available to other components ?
1. use element injector on consumer's compoenent -- > providers , componenet decorator.
2. Use it appcomponent or parent component's element injector- if we apply it on root component it will be singleton object.
3. Target root in @injectable('root') of service , so it can be accessed by all as singleton object.
4. use it @NgModule decorator's providers array - singleton object.
----------------------------------------------------------------------------------------
15 . What is Tree Shaking in Angular ?
It is a build process that will remove unused code from application.
If we register the services via @NgModule that it cannot be tree shakable , It will be hard to determine whether the service is used or not.
That is why from Angualr 6 they have introcuded another way to register the service using @injectable(root) -> now the services can be tree shaked.

------------------------------------------------------------------
16. How do you convert enter key act as submit button ?
1-> convert button type to submit
2 -> use form tag instead of div as container
-------------------------------------------------------
17. What is the value of !null in javascript ?
true.
-----------------------------------------------
18. What is BerhaviorSubject ?
It is same as Subject but allows us to pass paraemter while instantiating it.
------------------------------------------------------------------------
19. How do we find the number of subscribers for specific observable in Angualr ?
We can use Chrome dev tool to insspect the dom . There is a node called Observers -> This will gives how many subscribers are there for this observable.
------------------------------------------------------------------------------------------------------------------------------------------
20. How do you avoid subscribing same observable twice in template file ?
By using *ngIf and async approach.
We store observable value in parent tag and use alias to use it in inner html.
There is a drawback of this approach is the observable must emit non-false value . If it is emits false value then whole parent won't get render.
else part add ng-tenmplate ref of html portion.
------------------------------------------------------------------
21. What is the use of ng-template ?
It provides vitual parent container. It won't affect or change the structure of DOM.
We call it as silent parent.
-----------------------------------------
22. How do you pass JWT token in request ?
1-> request header ->using header variable such as x-access-token:localStorage['token']
2-> using cookies
-------------------------------------------------------------------------
23. How do you transform API response and your model in Angular ?
using Map operator in RXJS.
------------------------------------------------------------------
If component or DOM destroyed in half way subscribing to observable then we should resubscribe it
--------------------------------------------------------------------------------------------------------------
24. What is HTTP_interceptors ?
They are interface provided by angular to examine the current request and modify it.
---------------------------------------------------------------------------------------
25. What are the type of providers in Angular ?
1) Regular Providers 
2) Multi Provider - same DI token used for different instances.
------------------------------------------------------------------------------------
26. What are the type of injection tokens ?
1) Type Token 
2) String Token 
3) Injection Token.
----------------------------------------------------------------------
27. Can we run custom code during Angular bootstrap process ?
Yes, Angular exposing App_Initializer token service. By passing this token along with factory implementation in app module will enable us to execute the code during startup process.
-------------------------------------------------------------------------------------------
28. What is the difference between prod and debug build in Angualr ?
sourcemap files missing from prod builds - since they are being used in devtools for local debugging.
vendor.js to integrated in main build for prod.
all unused codes will removed.
--------------------------------------------------------------------------
29. How do you avoid Angular printing error messages in console ?
This can be overridden  by implementing custom Error Handler in application.
handleError method will be overridden.
----------------------------------------------------------------------------------------------
30. What is Component Oriented Style in Angular ?
There is a design principle called Container-Presentation Pattern which will help us further breakdown the feature componenets. so that the code can be managed.
A feature compoenent will be breakdown to two types of components --> 1) Container 2)Presentation
------------------------------------------------------------------------------------------------------------------
31. How do you pass data from parent component to child componenet ?
Using Input() decorator 
------------------------------------------------------------------------
32. How do you pass data from child componenet to parent component ?
Using Output() decorator with Event Emitter()--child has to raise an event.
---------------------------------------------------------------------------
33. What is eager loading ?
Loads all the components at once in Angular from the very beginning. this impact the performance.
single bundle file.
----------------------------------------------------------------------------
34. What is lazy loading ?
Load the components when it requires.
We need to do following steps to implement it.
a) Feature componenets must be grouped with feature modules. It means there will be other modules apart from root modules.
b) define child routes for each modules.
c) AppRoutes - load the modules as LoadChildren and import module file., AppRoutes will have only feature modules instead of components.
It reduces the initial load.
Bundling will generate seperate bundle for each modules in lazy loading.
------------------------------------------------------------------------------------------------
35 . How should we use eager loading and lazy loading ?
We should follow hybrid approach . 
We should not load everything eagrely and lazely alone.
If we use eager--> this will impact the performance.
If we use lazy alone - there is no point of using bundling.
---------------------------------------------------------------------
36. What is Pre-Loading ?
Loading the lazy loaded modules asynchronously in the background while the user interacting the app.
without preloading -- all lazy loaded modules will be downloaded on demand when user request.
with preloading - user no need to wait for modules to be downloaded.
We can override the preloading behavior - for eg: once pre loading kicked off - we can decide which module has to be preloaded.
----------------------------------------------------------------------
37. Components within modules is always visible to each other but they are not visible outside the module.
If we want to use particular component accessible outside the module then we have to mark it by exporting the component.
and cosumer module we will have to just import the module. when one module get imported into another module then all their public components
are accessible in parent module.

#
What are the various way of selecting elements(compoenent) in Angular ?
Answer:
- element itself : eg: select:'app-root'  this can be used in template like <app-root></app-root>
- as an atrribute: eg: select: '[app-root]' => <div app-root></div>
- as by class: eg select: '.app-root' => <div class="app-root"></div> 

`select by ID won't work in Angular`

#
what is the difference between ngOnInit and contructor ?

Answer:
   - Constructor should be used for initializing class instances . should not do actual work.
   - Angular Dependency Injector (DI) analyse the constructor parameters.
   - ngOnInit is a life cycle hook called by Angular to indicate that the Angular is done creating the component.
   - ngOnInit does not take any parameter.
   - In order to use OnInit we have to import it in the component class like this:
import {Component, OnInit} from ‘@angular/core’;









