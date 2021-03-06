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
    + Most apps strive for a consistent look across the application. Put your application-wide styles in styles.css (in src/environments folder).  A sample follows
    
        /* Application-wide Styles */
        
        h1 {
        
            color: #369;
            font-family: Arial, Helvetica, sans-serif;
            font-size: 250%;
        }
        
        h2, h3 {
        
            color: #444;
            font-family: Arial, Helvetica, sans-serif;
            font-weight: lighter;
        }
        
        body {
        
            margin: 2em;
        }
        
        body, input[text], button {
        
            color: #888;
            font-family: Cambria, Georgia;
        }
        
        /* everywhere else */
        
<\br>* {
            font-family: Arial, Helvetica, sans-serif;
        }

  + Individual components are stored in their own folder (ex. app/heroes).  This folder will contain three files the css, html and ts file corresponding to the style, template and class (typescript) files.  A typical class file is as follows:
  
      import { Component, OnInit } from '@angular/core';

      @Component({
      
        selector: 'app-heroes',
        templateUrl: './heroes.component.html',
        styleUrls: ['./heroes.component.css']
      })
      
      export class HeroesComponent implements OnInit {

        constructor() { }

        ngOnInit() {
        }

      }
      
  + You always import the Component symbol from the Angular core library and annotate the component class with @Component.

    + @Component is a decorator function that specifies the Angular metadata for the component.
    
  + Three metadata properties are specified in the file above:

    + selector— the component's CSS element selector
    + templateUrl— the location of the component's template file.
    + styleUrls— the location of the component's private CSS styles.
    
  + The CSS element selector, 'app-heroes', matches the name of the HTML element that identifies this component within a parent component's template.

  + The ngOnInit is a lifecycle hook. Angular calls ngOnInit shortly after creating a component. It's a good place to put initialization logic.

  + Always export the component class so you can import it elsewhere ... like in the AppModule
  
  + Add a hero property to the HeroesComponent for a hero named "Windstorm."

      + heroes.component.ts (hero property)

        + hero = 'Windstorm';
        
  + Show the hero. Open the heroes.component.html template file. Add data (for example to a header statement) binding to the new hero property.

    heroes.component.html

      My Heroes {{hero}}
      
  + Show the HeroesComponent view. To display the HeroesComponent, you must add it to the template of the shell AppComponent. Remember that app-heroes is the element selector for the HeroesComponent. So add an &lt;app-heroes&gt; element to the AppComponent template file, just below the title.

    src/app/app.component.html

    &lt;h1&gt;{{title}}&lt;/h1&gt;
    
      &lt;app-heroes&gt;&lt;/app-heroes&gt;
      
  + Create a Hero class.  A real hero is more than a name. Create a Hero class in its own file in the src/app folder. Give it id and name properties.

    src/app/hero.ts

    export class Hero {
    
      id: number;
      name: string;
      
    }
    
  + Return to the HeroesComponent class and import the Hero class. Refactor the component's hero property to be of type Hero. Initialize it with an id of 1 and the name Windstorm.

  + The revised HeroesComponent class file should look like this:

    src/app/heroes/heroes.component.ts

      import { Component, OnInit } from '@angular/core';
      
      import { Hero } from '../hero';

      @Component({
      
          selector: 'app-heroes',
          templateUrl: './heroes.component.html',
          styleUrls: ['./heroes.component.css']
          
      })
      
      export class HeroesComponent implements OnInit {
      
        hero: Hero = {
        id: 1,
        name: 'Windstorm'
        
      };

      constructor() { }

      ngOnInit() {
    
      }

    }
  
  + The page no longer displays properly because you changed the hero from a string to an object.
  
  + Show the hero object.  Update the binding in the template to announce the hero's name and show both id and name in a details layout like this:

    heroes.component.html (HeroesComponent's template)

     &lt;h2&gt;{{ hero.name }} Details &lt;/h2&gt;
     
     &lt;div&gt; &lt;span&gt;id:  &lt;/span&gt;{{hero.id}} &lt;/div&gt;
     
     &lt;div&gt; &lt;span&gt;name:  &lt;/span&gt;{{hero.name}} &lt;/div&gt;
    
  + The browser refreshes and display's the hero's information.
  
  + Format with the UppercasePipe.  Modify the hero.name binding like this.

    &lt;h2&gt;{{ hero.name | uppercase }} Details&lt;/h2&gt;

  + The browser refreshes and now the hero's name is displayed in capital letters. The word uppercase in the interpolation binding, right after the pipe operator ( | ), activates the built-in UppercasePipe.  Pipes are a good way to format strings, currency amounts, dates and other display data. Angular ships with several built-in pipes and you can create your own.
  
  + Edit the hero.  Users should be able to edit the hero name in an &lt;input&gt; textbox.  The textbox should both display the hero's name property and update that property as the user types. That means data flow from the component class out to the screen and from the screen back to the class.  To automate that data flow, setup a two-way data binding between the &lt;input&gt; form element and the hero.name property.

  + Two-way binding.  Refactor the details area in the HeroesComponent template so it looks like this:

    src/app/heroes/heroes.component.html (HeroesComponent's template)

    &lt;div&gt;
        
       &lt;label&gt;name:
       
       &lt;input [(ngModel)]="hero.name" placeholder="name"&gt;
         
       &lt;/label&gt;
       
    &lt;/div&gt;
        
  + [(ngModel)] is Angular's two-way data binding syntax.  Here it binds the hero.name property to the HTML textbox so that data can flow in both directions: from the hero.name property to the textbox, and from the textbox back to the hero.name.
  
  + Notice that the app stopped working when you added [(ngModel)].  To see the error, open the browser development tools and look in the console for a message like

      Template parse errors:
      
        Can't bind to 'ngModel' since it isn't a known property of 'input'.
        
  + Although ngModel is a valid Angular directive, it isn't available by default.  It belongs to the optional FormsModule and you must opt-in to using it.
  
  + AppModule -- Angular needs to know how the pieces of your application fit together and what other files and libraries the app requires. This information is called metadata.  Some of the metadata is in the @Component decorators that you added to your component classes. Other critical metadata is in @NgModule decorators.  The most important @NgModuledecorator annotates the top-level AppModule class which can be found in src/app/app.module.ts. This is where you opt-in to the FormsModule.
  
  + Import FormsModule.  Open AppModule (app.module.ts) and import the FormsModule symbol from the @angular/forms library.

    app.module.ts (FormsModule symbol import)

      import { FormsModule } from '@angular/forms'; // <-- NgModel lives here
      
  + Then add FormsModule to the @NgModule metadata's imports array, which contains a list of external modules that the app needs.

    app.module.ts ( @NgModule imports)

      imports: [
      
        BrowserModule,
        FormsModule
        
      ],

  + When the browser refreshes, the app should work again. You can edit the hero's name and see the changes reflected immediately in the &lt;h2&gt; above the textbox.

