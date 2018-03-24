# Angular_TypeScript
Repository for all things Angular.  This is basically a starting point for all resources related to Angular 2 and above (i.e. TypeScript version of Angular)

_ A good starting point may be this tutorial https://angular.io/tutorial (you can interactively edit it and see what happens)

_ Key aspects of Angular

  + Angular does not have a concept of "scope" or controllers, instead it uses a hierarchy of components as its primary architectural characteristic.
  + Angular has a different expression syntax, focusing on "[ ]" for property binding, and "( )" for event binding
  + Modularity – much core functionality has moved to modules
  + Angular recommends the use of Microsoft's TypeScript language, which introduces the following features:
    + Class-based Object Oriented Programming
    + Static Typing
    + Generics

  + It is based on TypeScript which is a superset of ECMAScript 6 (ES6), and is backwards compatible with ECMAScript 5 (i.e.: JavaScript). Angular also includes ES6:
  
    + Lambdas
    + Iterators
    + For/Of loops
    + Python-style generators
    + Reflection

  + Class
  + [[arrow functions ()=>]]
  + Asynchronous template compilation
  + Replacing controllers and $scope with components and directives – a component is a directive with a template
  + Iterative callbacks provided by RxJS. RxJS limits state visibility and debugging, but these can be solved with reactive add-ons like ngReact or ngrx.
  

_ Key Components

  + The application shell is the first page you see and it is controlled by an Angular component named AppComponent (in src/app folder). You'll find the implementation of the shell AppComponent distributed over three files:

    + app.component.ts— the component class code, written in TypeScript. Sample compnent file follows
    
        import { Component } from '@angular/core';

        @Component({
        
            selector: 'app-root',
            templateUrl: './app.component.html',
            styleUrls: ['./app.component.css']
        })
        
        export class AppComponent {
        
            title = 'Tour of Heroes';
        }
    + app.component.html— the component template, written in HTML.
    + app.component.css— the component's private CSS styles.

