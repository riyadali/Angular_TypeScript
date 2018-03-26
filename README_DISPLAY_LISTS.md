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