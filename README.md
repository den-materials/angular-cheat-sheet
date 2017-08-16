# angular-cheat-sheet

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

