<h1>MODULES</h1>

<p>An NgModule is a way to consolidate and organize information like components, directives, pipes, etc.  Some examples are the built in Angular libraries (like FormsModule, HttpModule, RouterModule)... and there are 3rd party modules as well. Modules can also add services to our applications.</p>

<h2>Module examples</h2>
<p>Every Angular app has at least one module: the root module (app module).  You bootstrap that module to launch the application (Angular sets this up for you!)</p>

<p>The BrowserModule includes the directives *ngIf and *ngFor, and luckily it's imported automatically for us when we set up an Angular app</p>

<p>Example of a module import: import { BrowserModule } from '@angular/platform-browser';</p>

<p>"Modules are a great way to provide services for all the module's components."  For example, if a module imports and provides a "game-logic-service", then all components within that module can use that service.</p>

<p>Another example:  Many applications capture information about the currently logged in user and make that information accessible through a user service.  This service could be provided by a module to all its children components.</p>