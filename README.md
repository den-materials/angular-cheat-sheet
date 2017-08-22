<h1>MODULES</h1>

<p>An NgModule is a way to consolidate and organize information like components, directives, pipes, etc.  Some examples are the built in Angular libraries (like FormsModule, HttpModule, RouterModule)... and there are 3rd party modules as well. Modules can also add services to our applications.</p>

<h2>Module examples</h2>
<p>Every Angular app has at least one module: the root module (app module).  You bootstrap that module to launch the application (Angular sets this up for you!)</p>

<p>The BrowserModule includes the directives *ngIf and *ngFor, and luckily it's imported automatically for us when we set up an Angular app</p>

<p>Example of a module import: import { BrowserModule } from '@angular/platform-browser';</p>

<p>"Modules are a great way to provide services for all the module's components."  For example, if a module imports and provides a "game-logic-service", then all components within that module can use that service.</p>

<p>Another example:  Many applications capture information about the currently logged in user and make that information accessible through a user service.  This service could be provided by a module to all its children components.</p>

# angular-cheat-sheet

# Observables && Promises

## promise
A Promise handles a single event when an async operation completes or fails. It is used in preference to callback functions in writing synchronus code. It returns a single value and is not cancellable. 

### syntax / methods
* new Promise(resolve, reject) => {}
* toPromise();
* then();
* pending
* fulfilled
* resolve
* rejected


## observable
An Observable is like a Stream and allows you to pass zero or more events where the callback is called for each event. It is cancellable. Uses Reactive Extensions (RxJS). Preferred over promises for Http requests. 

## How to construct an observable.
Here is an example of how you might create a really simple observable/subscription setup.
import {Component} from '@angular/core';
import {Observable} from 'rxjs/Observable';

@Component({
    selector: 'app',
    template: `
      <b>Angular Component Using Observables!</b>

      <h6 style="margin-bottom: 0">VALUES:</h6>
      <div *ngFor="let value of values">- {{ value }}</div>

      <h6 style="margin-bottom: 0">ERRORs:</h6>
      <div>Errors: {{anyErrors}}</div>

      <h6 style="margin-bottom: 0">FINISHED:</h6>
      <div>Finished: {{ finished }}</div>

      <button style="margin-top: 2rem;" (click)="init()">Init</button>
    `
})
export class MyApp {

  private data: Observable<Array<number>>;
  private values: Array<number> = [];
  private anyErrors: boolean;
  private finished: boolean;

  constructor() {
  }

  init() {
      this.data = new Observable(observer => {
          setTimeout(() => {
              observer.next(42);
          }, 1000);

          setTimeout(() => {
              observer.next(43);
          }, 2000);

          setTimeout(() => {
              observer.complete();
          }, 3000);
      });

      let subscription = this.data.subscribe(
          value => this.values.push(value),
          error => this.anyErrors = true,
          () => this.finished = true
      );
  }

}

### syntax
* Observable provides operators like map, forEach, reduce, similar to an array
* subscribe
* unsubscribe

SERVICES!

WHAT IS IT?
An Angular 2 service is simply a javascript function, along with its associated properties and methods, that can be included (via dependency injection) into Angular 2 components.

INJECTION?

INJECTABLE SERVICES:
The @Injectable() decorator tells TypeScript to emit metadata about the service. The metadata specifies that Angular may need to inject other dependencies into this service.

Code Example:
@Injectable()
export class NameService {
}



NAMING CONVENTION:
The naming convention for service files is the service name in lowercase followed by .service. For a multi-word service name, use lower dash-case. For example, the filename for SpecialSuperHeroService is special-super-hero.service.ts.
