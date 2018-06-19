# Module 14: Navigating Through Components

This module defines what navigation is and introduces the Angular Router used to navigate through our components.


## Structure 

The BookStore application is divided into a Java EE REST back-end (`bookstore-back`) and an Angular front-end (`bookstore-front`).


### Bookstore Front 

The code of this module follows the [Angular CLI](https://github.com/angular/angular-cli) directory structure. The `src/` directory contains the main source code. The `package.json` file is Node specific and it describes the project and its dependencies.

Once [Node JS](https://nodejs.org/en/) and a [Yarn](yarnpkg.com) are installed, enter the following commands:

* `yarn install`        : Installs all the dependencies (adding the node_modules directory)
* `ng serve`            : Executes the server. Go to [http://localhost:4200]()


## Demo 

* Change the component `app.component.html` file ``` <div class="container"> <div class="jumbotron"> <router-outlet></router-outlet> </div> </div> ```
* Add the routes to the `app-routing.module.ts` file ``` const routes: Routes = [ {path: '', component: BookListComponent}, {path: 'book-list', component: BookListComponent}, {path: 'book-detail/:bookId', component: BookDetailComponent}, {path: 'book-form', component: BookFormComponent} ]; ```
* Add the routerLink on the components : `app.component.html` ``` <a class="navbar-brand" [routerLink]="['/book-list']">{{title}}</a> <div class="collapse navbar-collapse" id="navbarCollapse"> <ul class="navbar-nav mr-auto"> <li class="nav-item"> <a class="nav-link" [routerLink]="['/book-list']">List</a> </li> <li class="nav-item"> <a class="nav-link" [routerLink]="['/book-form']">Create</a> ``` `book-detail.component.html` ``` <form (ngSubmit)="delete()"> <button type="submit" class="btn btn-primary">Delete</button> <a class="btn btn-secondary" [routerLink]="['/book-list']" role="button">Back</a> </form> ``` `book-form.component.html` ``` <form (ngSubmit)="create()"> <button type="submit" class="btn btn-primary">Create</button> <a class="btn btn-secondary" [routerLink]="['/book-list']" role="button">Cancel</a> </form> ``` `book-list.component.html` ``` <h5 class="mt-0 mb-1"><a [routerLink]="['/book-detail/1234']">book title</a></h5> ```
* Already introduce the router API by adding the create method in `book-form.component.ts` ``` constructor(private router: Router) { } create() { this.router.navigate(['/book-list']); } ``` And in `book-detail.component.ts` ``` constructor(private router: Router) { } delete() { this.router.navigate(['/book-list']); } ```

*To execute the application you have to build it (`mvn clean package`) and then deploy the `bookstore-back.war` into [WildFly](https://wildfly.org).*
