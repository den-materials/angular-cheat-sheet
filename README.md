# WDI Angular Cheat Sheet

# Components

A component controls a patch of screen called a view.
You define a components application logic inside a class. The class interacts with the view through an API of properties and methods. 

Properties can return data through imported services.
Methods will set properties based on user input. 

Components are created, updated, and destoryed as a user moves through the application. The app takes action at each moment in its lifecycle through optional lifecycle hooks(ex. ngOnInit()).

For Documentation on Angular components visit: https://angular.io/guide/architecture#components

## Angular CLI
[documentation](https://github.com/angular/angular-cli/wiki)

### Overview

The Angular CLI is a tool to initialize, develop, scaffold and maintain Angular applications

### Getting Started

To install the Angular CLI:

`npm install -g @angular/cli`

Generating and serving an Angular project via a development server Create and run a new project:

```
ng new my-project
cd my-project
ng serve
```

Navigate to http://localhost:4200/. The app will automatically reload if you change any of the source files.

### Common commands

Generate a new component, service, modules:
```ng generate component <name>
ng generate service <name>
ng generate module <name>
```
or use shorhand generation commands:
`ng g c <name>`

Run all jasmine tests:
`ng test`

Build/compile app into an output directory (`dist/`):
`ng build`

### Config
You can use the `angular-cli.json` file to configure css and javascript libraries like Bootstrap and jQuery.

For example, to use bootstrap you would:
`npm install bootstrap`
Then add the following to the `styles` array in `angular-cli.json`
```
"styles": [
  "styles.css",
  "../node_modules/bootstrap/dist/css/bootstrap.css"
]
```

### Other helpful commands
Search the angular documentation:
`ng doc 'search term'`
GitHub
angular/angular-cli
angular-cli - CLI tool for Angular

## Routing

Overview
------

The browser is a familiar model of application navigation:

Enter a URL in the address bar and the browser navigates to a corresponding page.
Click links on the page and the browser navigates to a new page.
Click the browser's back and forward buttons and the browser navigates backward and forward through the history of pages you've seen.
The Angular Router ("the router") borrows from this model. It can interpret a browser URL as an instruction to navigate to a client-generated view. It can pass optional parameters along to the supporting view component that help it decide what specific content to present. You can bind the router to links on a page and it will navigate to the appropriate application view when the user clicks a link. You can navigate imperatively when the user clicks a button, selects from a drop box, or in response to some other stimulus from any source. And the router logs activity in the browser's history journal so the back and forward buttons work as well.

Routing
--------

First you need to import the routing package from the anuglar/router package.
ex.... "import { RouterModule, Routes } from '@angular/router';"

Second, you need a base URL of '/' defined in your index.html file:
```//index.html (Somewhere in the head)
<head>
  <base href="/">
```

Your app module is the file that will contain all of your front-end routes, much like your routes file on the back-end. But before we go about defining routes, we have to tell Angular that we are interested in using its optional front-end routing library. To do that, we need to import that library, and in the NgModule decorator's (`@NgModule`) imports array, specify that our route paths will be constructed on the root ('/' -- our root path that we defined above). Then, remember how routes consist of 1), a URL path and 2), an HTTP verb associated with it? The routes in your app module will similarly have a path, but you'll be loading (i.e., "getting") a component instead. But, remember that if you're loading a component when you hit that URL path, our route will have to know about that component, so you'll have to import that component as well.

```//app.module.ts
import { RouterModule } from '@angular/router'; //tell Angular that you want to use the routing library (it doesn't come with Angular out of the box)
import { PuppiesComponent } from './puppies.component'; //import any components that your routes will be hitting, so that this file knows what we're talking about

@NgModule({
  imports: [
  ..., //other modules
  RouterModule.forRoot([ //this function appends the paths below to the base URL we defined in our index.html file above
    {
      path: 'puppies', //appends 'puppies' to '/' -> '/puppies'
      component: PuppiesComponent //So, when we hit /puppies in the URL bar, we will be rendering the PuppiesComponent
    }
  ])
})
```

When you're defining routes in this manner, start with more specific routes and end with those that are less specific (those that take in route parameters, or, i.e., puppies/edit/:id), because the router uses a first-match wins strategy.

## Angular Universal

SEO Optimization: Search engines won't be able to scrape single-page apps; "server-side pre-rendering  is a reliable, flexible, and efficient way to ensure that all search engines can access your content." ~Google, Angular Universal Docs

Allows devs to transition from the server view to the client view in the browser.

The best of both worlds: the user experience and high performance of an SPA, combined with the SEO friendliness of a static page.

Terminal
```
npm install -g universal-cli
```

Once installed, use ung instead of ng to serve, generate components, directives, modules, etc.

E.g. `ung serve --open`

## More Angular Universal

The Angular Universal project consists of the base platform API and the surrounding tools that enables developer to do server side rendering(or pre-rendering) of Angular applications. The platform API part has been merged into Angular core as of 4.0.

### At a high level, there are two major pieces to the Angular Universal:

1. Rendering on the server which means generating all the HTML for a page at a given route.
2. Transitioning from the server view to the client view in the browser client

### The basic idea is to build an app that does not just render to server but also runs on the server.  In Angular 2, this is achieved with the help of Angular Universal which loads our app on the server first, and then drops it to the browser once ready.  

### Highlights:

- Better perceived performance
    - First time users will instantly see a server rendered view which greatly improves perceived performance.  According to Google research, the difference of just 200 milliseconds in page load performance has an impact on user behavior. 
- Optimized for Search Engines
    - Server-side pre-rendering is a reliable, flexible and efficient way to ensure that all search engines can access your content.
- Site Preview
    - Ensure that Facebook, Twitter and all other social media apps correctly display a preview image of your app.

## service worker
a stand alone javascript program that you can run in your browser. it can handle background / network tasks for you website / web-app. service workers allow functionality offline and can speed up your app by using cached files if there has been no change.

place in index.html file of your app:
```
<script>
  if ('serviceWorker' in navigator) {
    navigator.serviceWorker.register('/service-worker.js').then(function(registration) {
      console.log('Service Worker registered');
    }).catch(function(err) {
      console.log('Service Worker registration failed: ', err);
    });
  }
</script>
```

in your angular-cli.json add service worker to your assets:
```
"assets": [
  "assets",
  "favicon.ico",
  "service-worker.js"
],
```

links:
- https://www.npmjs.com/package/@angular/service-worker
- https://pascalprecht.github.io/slides/angular-and-service-workers/#/a
- https://coryrylan.com/blog/fast-offline-angular-apps-with-service-workers

# TypeScript

TypeScript is a superset of of JavaScript that transpiles to vanilla JavaScript

Since TypeScript is a superset of JavaScript, any valid JavaScript is also valid TypeScript

TypeScript was developed by and is maintained by Microsoft

Released in 2012

TypeScript adds optional types, classes, and modules to JavaScript 

        class Person {
            private name: string;
            private age: number;
            private salary: number;

            constructor(name: string, age: number, salary: number) {
                this.name = name;
                this.age = age;
                this.salary = salary;
            }

It is transpiled using the command "tsc"

When transpiles, it makes ES6 features ES5 compatible (which is awesome)

<h1>MODULES</h1>

<p>An NgModule is a way to consolidate and organize information like components, directives, pipes, etc.  Some examples are the built in Angular libraries (like FormsModule, HttpModule, RouterModule)... and there are 3rd party modules as well. Modules can also add services to our applications.</p>

<h2>Module examples</h2>
<p>Every Angular app has at least one module: the root module (app module).  You bootstrap that module to launch the application (Angular sets this up for you!)</p>

<p>The BrowserModule includes the directives *ngIf and *ngFor, and luckily it's imported automatically for us when we set up an Angular app</p>

<p>Example of a module import: import { BrowserModule } from '@angular/platform-browser';</p>

<p>"Modules are a great way to provide services for all the module's components."  For example, if a module imports and provides a "game-logic-service", then all components within that module can use that service.</p>

<p>Another example:  Many applications capture information about the currently logged in user and make that information accessible through a user service.  This service could be provided by a module to all its children components.</p>

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

### Helpful Resources

- [A good article explaining Angular Observables](https://hackernoon.com/understanding-creating-and-subscribing-to-observables-in-angular-426dbf0b04a3)
	- Observables are like newsletters that people can subscribe to. for each new subscription, a new newsletter is printed and sent out. 
- [Another take on Observable diagrams](https://gadenver.slack.com/files/U7ZDLDEBV/F8YSERTHQ/ewn3b.png)
- [When is a promise a better choice?](https://netbasal.com/angular-stop-using-observable-when-you-should-use-a-promise-8da0788a8d2)
- [Angular Observable Intro](https://developer.telerik.com/topics/web-development/introduction-observables-angular-developers/)

### Conclusion

- Both deal with asynchronous nature of applications but in different ways
	- promises return one set value
	- observables return multiple values over time
- Promises can be used in most cases, don't wanna overuse observables
- Both push data (initiate from the data creator)
- promises take in data and spit out a value
- observables originate an event and publish it to subscribers
- observables are lazy and only do something when something subscribes to listen to changes
- observables can be cancelled, promises cannot

# SERVICES!

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

## JASMINE/Testing

The Jasmine test framework provides everything needed to write basic tests for Angular. It ships with an HTML test runner that executes tests in the browser. 

#### Compare Jasmine and Mocha
	- Similarities:
		- Both use describe, it, before, beforeeach, each
	- Differences: 
		- Punctuation is different to.Equal vs toEqual
		- Jasmine uses ES6 and Mocha uses ES5
		- Jasmine opens a new window browser, mocha is just in Terminal
		- Jasmine comes with its' own assertion library (which is why it is to.Equal)
		
- Use $ng test to run the testing suite
- Helpful links and readings
	- [Official angular docs](https://angular.io/guide/testing)
- For end 2 end testing (ie acceptance tests), they use protractor not Jasmine. In e2e testing, one process runs the real application and a second process runs protractor tests that simulate user behavior and assert that the application respond in the browser as expected.
- Sample unit test in [doghouse](https://github.com/den-materials/angular/blob/master/lectures/03-observables-tdd-universal/02-jasmine-and-tdd.md) 

### Syntax Example:

 describe(‘1st tests’, () => {
 
  it(‘true is true’, () => expect(true).toBe(true));
  
});

### Conclusion:

![pasted image at 2017_11_02 02_44 pm](https://user-images.githubusercontent.com/31824846/32349634-5ca2ea08-bfdd-11e7-86c6-60818c8e611c.png)
