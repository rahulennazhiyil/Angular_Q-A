# Angular_Q-A
Angular_Q&amp;A

     _                      _                 ____ _     ___
    / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
   / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
  / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
 /_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
                |___/


Angular CLI:

![image](https://github.com/user-attachments/assets/dbd6de5c-107e-4438-a02f-20b9d269cd32)
* Sequence of Loading Angular
1. index.html: The main HTML file that includes the root element where the Angular app will be bootstrapped.
2. main.ts: The entry point that bootstraps the Angular application.
3. app.module.ts: The root module that declares and imports all necessary modules and components.
4. app.component.ts: The root component that serves as the main view of the application.
This sequence ensures that the Angular application is properly initialized and ready to run.

* Types of Directives
--> Components: These are directives with a template. They are the most common type of directive.
--> Attribute Directives: These change the appearance or behavior of an element, component, or another directive.
--> Structural Directives: These change the DOM layout by adding and removing DOM elements.

Examples
--------
1. Component Directive
----------------------
A component is a directive with a template. For example, the AppComponent is a component directive.

2. Attribute Directives
Attribute directives change the appearance or behavior of an element. Common attribute directives include NgClass, NgStyle, and NgModel.
--> NgClass: Adds and removes a set of CSS classes.
--> NgStyle: Adds and removes a set of HTML styles.
--> NgModel: Adds two-way data binding to an HTML form element.

3. Structural Directives
------------------------
Structural directives change the DOM layout by adding and removing DOM elements. Common structural directives include NgIf, NgFor, and NgSwitch.

--> NgIf: Conditionally includes a template based on the value of an expression.
--> NgFor: Repeats a template for each item in a list.
--> NgSwitch: Switches between alternative views based on a value.

Creating a Custom Directive
---------------------------
You can also create your own custom directives. Here’s an example of a simple attribute directive that changes the background color of an element when it is hovered over.
Generate the Directive:
** ng generate directive highlight

Implement the Directive:
TypeScript
Plain Text
// src/app/highlight.directive.ts
import { Directive, ElementRef, HostListener } from '@angular/core';
@Directive({
  selector: '[appHighlight]'})export class HighlightDirective {
  constructor(private el: ElementRef) {}
  @HostListener('mouseenter') onMouseEnter() {
    this.highlight('yellow');
  }
  @HostListener('mouseleave') onMouseLeave() {
    this.highlight('');
  }
  private highlight(color: string) {
    this.el.nativeElement.style.backgroundColor = color;
  }
}
 
HTML
----
<p appHighlight>Hover over this text to see the highlight effect.</p>
 
Angular lifecycle hooks
-----------------------

Angular lifecycle hooks are special methods that Angular calls at specific points in the lifecycle of a component or directive. These hooks allow you to tap into key events and perform custom operations during the creation, update, and destruction of components.
-> Key Lifecycle Hooks
   -------------------
1. ngOnChanges: Called before ngOnInit and whenever one or more data-bound input properties change.
2. ngOnInit: Called once, after the first ngonChanges
3. ngDoCheck: Called during every change detection run, immediately after ngonChanges and ngOnInit
4. ngAfterContentInit: Called once after the first ngDoCheck
5. ngAfterContentChecked: Called after ngAfterContentInit and every subsequent ngDoCheck.
6. ngAfterViewInit: Called once after the first ngAfterContentChecked
7. ngAfterViewChecked: Called after ngAfterViewInit and every subsequent ngAfterContentChecked.
8. ngOnDestroy: Called just before Angular destroys the component.


==> What is Angular?
* Angular is a TypeScript-based front-end web application framework.
* It’s used for designing single-page applications (SPAs) and offers features like components, services, modules, and routing.

==> How does an Angular application work?
* Every Angular app has an angular.json file that contains configurations. The builder looks at this file to find the entry point of the application.
* The entry point is usually the main.ts file, where Angular bootstraps the app by calling platformBrowserDynamic().bootstrapModule(AppModule).

==> What are Angular components?
* Components are the building blocks of an Angular app. They encapsulate HTML, CSS, and logic.
* To create a component, use the Angular CLI command: ng generate component component-name.

==> What is data binding in Angular?
* Data binding connects the UI (template) with the component’s data. Types of data binding: Interpolation, Property binding, Event binding, and Two-way binding.

==> What is Angular CLI?
* Angular CLI (Command Line Interface) is a powerful tool for creating, managing, and building Angular projects.
* Use ng new to create a new project and ng serve to run it locally.

==> What is lazy loading in Angular?
* Lazy loading loads modules only when needed, improving app performance.
* Use the loadChildren property in the route configuration to enable lazy loading.

==> What is Angular service?
* Services provide reusable logic and data to components.
* Create a service using ng generate service service-name.

==> What is dependency injection in Angular?
* Dependency injection (DI) is a design pattern where components receive their dependencies from an external source (usually a service).
* Angular’s DI system manages the injection of services into components.

==> How do you handle HTTP requests in Angular?
* Use Angular’s HttpClientModule to make HTTP requests.
Example:
TypeScript
import { HttpClient } from '@angular/common/http';
constructor(private http: HttpClient) {
  this.http.get('https://api.example.com/data').subscribe(response => {
    console.log(response);
  });
}

==> What are Angular directives?
* Directives are instructions in the DOM. Examples: *ngFor, *ngIf, and custom directives.
* Custom directives can be created using @Directive decorator.


BASIC COMMANDS USED IN ANGULAR
------------------------------

** ng new <project-name>: 
==> Creates a new Angular workspace and generates a new application skeleton. Replace <project-name> with your desired project name.
** ng serve:
==> Builds and serves your Angular application locally. It automatically rebuilds the app and reloads the page when you make changes to the source files. Access it at http://localhost:4200/.
** ng generate <schematic>:
==>  Generates various parts of your application, such as components, services, modules, and more. For example:
** ng generate component my-component: 
==> Creates a new component.
** ng generate service my-service: 
==> Generates a new service.
** ng build: Compiles your application into an output directory (usually dist/). Use the --prod flag for production builds.
