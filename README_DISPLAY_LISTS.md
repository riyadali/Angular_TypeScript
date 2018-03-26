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
      + Add an <h2> at the top,
      + Below it add an HTML unordered list (<ul>)
      + Insert an <li> within the <ul> that displays properties of a hero.
      + Sprinkle some CSS classes for styling (you'll add the CSS styles shortly).
    + Make it look like this:

        heroes.component.html (heroes template)

            <h2>My Heroes</h2>
            <ul class="heroes">
              <li>
                  <span class="badge">{{hero.id}}</span> {{hero.name}}
              </li>
            </ul>
            
    + Now change the <li> to this:

            <li *ngFor="let hero of heroes">
            
    + The *ngFor is Angular's repeater directive. It repeats the host element for each element in a list. In this example
      + <li> is the host element
      + heroes is the list from the HeroesComponent class.
      + hero holds the current hero object for each iteration through the list.
    + Don't forget the asterisk (*) in front of ngFor. It's a critical part of the syntax. After the browser refreshes, the list of heroes appears.  
