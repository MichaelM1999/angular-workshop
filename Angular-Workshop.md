# Angular Workshop

#### Goals 
1. Create an Angular enviornment
2. Create Components
3. Utilize Angular Routing

## Documentation
[Docs](https://angular.io/docs)

## spin up enviornment using CLI
1. ng new demo-app
2. cd demo-app, ng serve

## Create Hello World App
1. delete angular html scss and js file
2. change the app.component.ts templateurl to template and write hello
        world in back ticks (these things)->``
3. show hello world app

## Create Dashboard Component
1. create new folder called Components in the SRC folder
2. with in Components Create the dashboard folder
3. create three files in dashboard called dashboard.ts dashboard.html
    and dashboard.scss.
4. inside dashboard.ts import Component from @angular/core
    ```
    import { Component } from '@angular/core';
    ```
5. create component
    ```
    @Component({
        selector:'Dashboard',
        templateUrl:'./dashboard.html'
        stylesUrls:['./dashboard.scss']
    })
    export class Dashboard {

    }
    ```
6. create the html in Dashboard.html
7. register the component in the app Module IMPORTANT!!
8. now that the first component is created and registered we can use it
9. go to the app.component.ts and change the hello world template to 
    `<Dashboard></Dashboard>`
    this will tell angular to load the dashboard Component based on the selector you assigned it!

## Create a new component called info so we can provide some random text
1. complete step 5 again with reference to Info rather then Dashboard

## Angular Routing
1. create navbar Component the same way we did for info and dashboard
    do not worry about the html yet we will get back to this to add the a tags
2. we need to utilize the angular routing feature
3. create a file called routes.ts in the app folder
4. in the routes.ts file we need to import Routes from @angular/routes, and any
    components we might need
    ```
    import { Routes } from '@angular/routes'
    import { Dashboard } from '../src/components/dashboard/dashboard'
    ```
5. create the first route looks something like this 
    ```
    export const appRoutes:Routes = [
        { path: 'dashboard', component: Dashboard }
    ]
    ```
6. we should also add a default route so when the route is blank we load  something.
    ```
        export const appRoutes:Routes = [
        { path: '', redirectTo: '/dashboard', pathMatch:'full' },
        { path: 'dashboard', component: Dashboard }
    ]
    ```
7. To make these work we need to register the routes in the app module
    inside the app module import appRoutes from './routes.ts' as well as
    ```
    import RouterModule from 'angular/router'
    ```
8. lastly in the imports array add the line 
    ```
    RouterModule.forRoot(appRoutes);
    ```

## Wiring the Navbar
1. within the navbar html we need to add some a tags that look like this
    ```
    <a [routerLink]="['/dashboard']" routerLinkActive="active">Dashboard</a>
    ```
2. the routerLinkActive="active" tells angular when this is the active route the
    style class assigned to this element is changes to active we call this by putting a.active in the scss file
3. add an a tag for each route that we want a separte page for.
4. go to website and test at this point we have made a hello world app and
    successfully created a working angular app with two pages a navbar and working routing.