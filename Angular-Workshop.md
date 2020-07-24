    Angular Workshop

        by the end of the workshop everyone should have an understanding of how to create an angular enviornment,create components and utilize angular routing.

1. introductions (Name, where you're from, coding background)

2. Angular intro (documentation)

3. spin up enviornment using CLI
    3a. ng new demo-app
    3b. cd demo-app, ng serve

4. Create Hello World App
    4a. delete angular html scss and js file
    4b. change the app.component.ts templateurl to template and write hello
        world in back ticks (these things)->``
    4c. show hello world app
5. Create Dashboard Component
    5a. create new folder called Components in the SRC folder
    5b. with in Components Create the dashboard folder
    5c. create three files in dashboard called dashboard.ts dashboard.html
        and dashboard.scss.
    5d. inside dashboard.ts import Component from @angular/core
        // import { Component } from '@angular/core';
    5e. create component
        @Component({
            selector:'Dashboard',
            templateUrl:'./dashboard.html'
            stylesUrls:['./dashboard.scss']
        })
        export class Dashboard {

        }
    5f. create the html in Dashboard.html
    5g. register the component in the app Module IMPORTANT!!
6. now that the first component is created and registered we can use it
    6a. go to the app.component.ts and change the hello world template to 
    // `<Dashboard></Dashboard>`
    this will tell angular to load the dashboard Component based on the selector you assigned it!
7. Create a new component called info so we can provide some random text
    7a. complete step 5 again with reference to Info rather then Dashboard
8. now we need a way to get to these components separetly we will need some kind 
    of navbar and routing system
9. create navbar Component the same way we did for info and dashboard
    do not worry about the html yet we will get back to this to add the a tags
10. we need to utilize the angular routing feature
    10a. create a file called routes.ts in the app folder
    10b.in the routes.ts file we need to import Routes from @angular/routes, and any components we might need
    // import { Routes } from '@angular/routes'
    // import { Dashboard } from '../src/components/dashboard/dashboard'
    10c. create the first route looks something like this 
    export const appRoutes:Routes = [
        { path: 'dashboard', component: Dashboard }
    ]
    10d. we should also add a default route so when the route is blank we load  something.
        export const appRoutes:Routes = [
        { path: '', redirectTo: '/dashboard', pathMatch:'full' },
        { path: 'dashboard', component: Dashboard }
    ]
    10e. To make these work we need to register the routes in the app module
    inside the app module import appRoutes from './routes.ts' as well as
    import RouterModule from 'angular/router'
    10f. lastly in the imports array add the line 
    //  RouterModule.forRoot(appRoutes)
11. now if we look at the app we can change the routes manually but this isnt effiecient so we need to wire up the navbar
12. within the navbar html we need to add some a tags that look like this
    // <a [routerLink]="['/dashboard']" routerLinkActive="active">Dashboard</a>
    12a. the routerLinkActive="active" tells angular when this is the active route the style class assigned to this element is changes to active we call this by putting a.active in the scss file
    12b. add an a tag for each route that we want a separte page for.
13. go to website and test at this point we have made a hello world app and successfully created a working angular app with two pages a navbar and working routing.
14. answer questions people may have.
15. if time permits go over *ngIf=""
16. if time permits go over ngOnint
    // export class navbar implements Oninit {
    //
    //}
17. if time permits go over services 
    //     constructor(private http: HttpClient){
    //
    //}
