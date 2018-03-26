# Display a Heroes List
In this page, you'll expand the Tour of Heroes app to display a list of heroes, and allow users to select a hero and display the hero's details

_ Create mock heroes.  You'll need some heroes to display. Eventually you'll get them from a remote data server. For now, you'll create some mock heroes and pretend they came from the server.
  + Create a file called mock-heroes.ts in the src/app/ folder. Define a HEROES constant as an array of ten heroes and export it. The file should look like this.
  
    src/app/mock-heroes.ts

    import { Hero } from './hero';

    export const HEROES: Hero[] = [
    
      { id: 11, name: 'Mr. Nice' },
      
      { id: 12, name: 'Narco' },
      
      { id: 13, name: 'Bombasto' },
      
      { id: 14, name: 'Celeritas' },
      
      { id: 15, name: 'Magneta' },
      
      { id: 16, name: 'RubberMan' },
      
      { id: 17, name: 'Dynama' },
      
      { id: 18, name: 'Dr IQ' },
      
      { id: 19, name: 'Magma' },
      
      { id: 20, name: 'Tornado' }
      
    ];
    
_ Displaying heroes.  You're about to display the list of heroes at the top of the HeroesComponent.
  + Open the HeroesComponent class file and import the mock HEROES.

      src/app/heroes/heroes.component.ts (import HEROES)

          import { HEROES } from '../mock-heroes';
          
  + Add a heroes property to the class that exposes these heroes for binding.

      heroes = HEROES;
      
_ List heroes with *ngFor:
  + Open the HeroesComponent template file and make the following changes: 
    + Add an &lt;h2&gt; at the top,
    + Below it add an HTML unordered list (&lt;ul&gt;)
    + Insert an &lt;li&gt; within the &lt;ul&gt; that displays properties of a hero.
    + Sprinkle some CSS classes for styling (you'll add the CSS styles shortly).
  + Make it look like this:

    heroes.component.html (heroes template)

      &lt;h2&gt;My Heroes&lt;/h2&gt;
      
      &lt;ul class="heroes"&gt;
      
       &lt;li&gt;
        
       &lt;span class="badge">{{hero.id}}&lt;/span&gt; {{hero.name}}
          
       &lt;/li&gt;
        
      &lt;/ul&gt;
      
  + Now change the &lt;li&gt; to this:
  
      &lt;li *ngFor="let hero of heroes"&gt;
      
  + The *ngFor is Angular's repeater directive. It repeats the host element for each element in a list.  In this example

    + &lt;li&gt; is the host element
    + heroes is the list from the HeroesComponent class.
    + hero holds the current hero object for each iteration through the list.
    
  + Don't forget the asterisk (*) in front of ngFor. It's a critical part of the syntax.  After the browser refreshes, the list of heroes appears.
  
_ Style the heroes.  The heroes list should be attractive and should respond visually when users hover over and select a hero from the list. In the first tutorial, you set the basic styles for the entire application in styles.css. That stylesheet didn't include styles for this list of heroes.  You could add more styles to styles.css and keep growing that stylesheet as you add components.  You may prefer instead to define private styles for a specific component and keep everything a component needs— the code, the HTML, and the CSS —together in one place. This approach makes it easier to re-use the component somewhere else and deliver the component's intended appearance even if the global styles are different.

  + You define private styles either inline in the @Component.styles array or as stylesheet file(s) identified in the @Component.styleUrls array.
  + When the CLI generated the HeroesComponent, it created an empty heroes.component.css stylesheet for the HeroesComponent and pointed to it in @Component.styleUrls like this.
  
    src/app/heroes/heroes.component.ts (@Component)

        @Component({
            selector: 'app-heroes',
            templateUrl: './heroes.component.html',
            styleUrls: ['./heroes.component.css']
        })
        
  + Open the heroes.component.css file and paste in the private CSS styles for the HeroesComponent. You'll find them in the final code review at the bottom of this guide.
