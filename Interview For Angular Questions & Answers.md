# 🅰️ Angular Interview Questions and Answers

A comprehensive collection of Angular interview questions and answers to help you prepare for your next interview.

## 📋 Table of Contents

- [Basic Concepts](#basic-concepts)
- [Components and Templates](#components-and-templates)
- [Directives](#directives)
- [Services and Dependency Injection](#services-and-dependency-injection)
- [Routing](#routing)
- [Forms](#forms)
- [HTTP and Observables](#http-and-observables)
- [Angular Modules](#angular-modules)
- [Performance and Optimization](#performance-and-optimization)
- [Miscellaneous](#miscellaneous)
- [Advanced Concepts](#advanced-concepts)
- [Architecture and Best Practices](#architecture-and-best-practices)
- [Testing](#testing)
- [Real-World Challenges](#real-world-challenges)

## Basic Concepts

### What is Angular, and how is it different from AngularJS?
Angular is a TypeScript-based front-end framework for building dynamic single-page applications. AngularJS (v1.x) is based on JavaScript and uses a two-way binding architecture. Angular offers improved performance with Ahead-of-Time (AOT) compilation, component-based architecture, and dependency injection.

### What are the building blocks of Angular?
The primary building blocks of Angular are:
- Modules (NgModules)
- Components
- Templates
- Directives
- Services
- Dependency Injection
- Pipes
- Routing

### Explain the difference between components and directives.
- **Components**: Control views, have templates and styles, and are the main building blocks of UI.
- **Directives**: Modify behavior or appearance of DOM elements.
  - **Structural Directives**: Change DOM structure (e.g., *ngIf, *ngFor).
  - **Attribute Directives**: Change appearance or behavior of an element (e.g., ngClass, ngStyle).

### What is data binding, and what are its types?
Data binding links UI and application logic. Types:
- **Interpolation**: `{{data}}` (one-way from component to view)
- **Property Binding**: `[property]="expression"` (one-way)
- **Event Binding**: `(event)="handler()"` (one-way from view to component)
- **Two-Way Binding**: `[(ngModel)]="property"` (two-way)

### What is the purpose of Angular CLI? Can you name some CLI commands?
CLI automates app creation, testing, and deployment. Common commands:
- `ng new <app-name>`: Creates a new Angular app
- `ng serve`: Runs the application locally
- `ng generate <component|service> <name>`: Generates components or services
- `ng build`: Builds the project for deployment
- `ng test`: Runs unit tests

### What is TypeScript, and why is it used in Angular?
TypeScript is a superset of JavaScript that adds static typing. Angular uses TypeScript for better tooling, maintainability, and early error detection.

## Components and Templates

### What is a component? How do you create and use it?
A component is the fundamental building block of Angular's UI. It controls a part of the UI with its template and logic.
- Create: `ng generate component <name>`
- Use: Add the selector (e.g., `<app-name></app-name>`) in the HTML.

### Explain the role of @Input() and @Output() decorators.
- **@Input()**: Pass data from a parent to a child component.
- **@Output()**: Emit events from a child to a parent using EventEmitter.

### What is the difference between template-driven forms and reactive forms?
- **Template-Driven Forms**: Define forms in the HTML template; simpler for small forms.
- **Reactive Forms**: Define forms in the component class using FormGroup and FormControl; better for dynamic and complex forms.

### How do you handle events in Angular templates?
Use event binding syntax: `(event)="handlerFunction()"`. Example: 
```html
<button (click)="onClick()">Click Me</button>
```

### What are lifecycle hooks? Can you name and explain their purposes?
Lifecycle hooks allow developers to tap into component events:
- **ngOnInit()**: Executes after component initialization
- **ngOnChanges()**: Executes when input properties change
- **ngOnDestroy()**: Executes just before component destruction

### How would you implement conditional rendering in an Angular template?
Use *ngIf:
```html
<div *ngIf="condition">Content</div>
```

## Directives

### What are Angular directives, and how are they classified?
Directives are instructions to manipulate the DOM:
- **Structural Directives**: Modify DOM structure (e.g., *ngIf, *ngFor)
- **Attribute Directives**: Modify element behavior or appearance (e.g., ngStyle, ngClass)

### What is the difference between structural and attribute directives?
- **Structural**: Change the DOM layout (add/remove elements)
- **Attribute**: Change the appearance or behavior of an element

### How do you create a custom directive?
Use @Directive decorator:
```typescript
@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
  constructor(el: ElementRef) {
    el.nativeElement.style.backgroundColor = 'yellow';
  }
}
```

### Explain the purpose of ngIf, ngFor, and ngClass.
- **ngIf**: Conditionally adds/removes elements
- **ngFor**: Iterates over a list
- **ngClass**: Dynamically applies classes

## Services and Dependency Injection

### What is a service in Angular, and how do you create one?
A service contains reusable business logic. Create it using CLI:
```bash
ng generate service serviceName
```

### What is dependency injection, and how does Angular implement it?
DI is a design pattern where dependencies are provided to a class rather than created by it. Angular implements DI using the injector hierarchy.

### What is the purpose of a singleton service?
A singleton service ensures that a single instance of the service is shared across the app.

### Explain the difference between providedIn: 'root' and providing a service in a specific module.
- **providedIn: 'root'**: Makes the service available app-wide
- **Providing in a module**: Restricts availability to that module

## Routing

### How does routing work in Angular?
Angular routing allows navigation between views within a single-page application:
```typescript
const routes: Routes = [
  { path: 'home', component: HomeComponent },
  { path: 'about', component: AboutComponent },
  { path: '', redirectTo: 'home', pathMatch: 'full' }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule {}
```

### What is the purpose of RouterModule and Routes?
- **RouterModule**: Provides necessary services and directives for routing
- **Routes**: Defines the mapping of URL paths to components

### How do you implement lazy loading in Angular?
Lazy loading loads feature modules only when their route is accessed:
```typescript
const routes: Routes = [
  { path: 'admin', loadChildren: () => import('./admin/admin.module').then(m => m.AdminModule) }
];
```

### What are route guards, and what types of guards are available?
Guards control navigation to/from routes based on conditions:
- **CanActivate**: Controls if a route can be activated
- **CanActivateChild**: Controls if child routes can be activated
- **CanDeactivate**: Controls if a user can leave a route
- **Resolve**: Pre-fetches data before route activation
- **CanLoad**: Controls if a module can be lazy-loaded

### How do you pass parameters in Angular routes?
**Route Parameters**:
```typescript
// Define route with parameter
const routes: Routes = [
  { path: 'profile/:id', component: ProfileComponent }
];

// Access parameter in component
constructor(private route: ActivatedRoute) {}
ngOnInit() {
  this.route.params.subscribe(params => {
    console.log(params['id']);
  });
}
```

**Query Parameters**:
```typescript
// HTML template
<a [routerLink]="['/profile']" [queryParams]="{ id: 123 }">Profile</a>

// Component
constructor(private route: ActivatedRoute) {}
ngOnInit() {
  this.route.queryParams.subscribe(params => {
    console.log(params['id']);
  });
}
```

## Forms

### What is the difference between reactive forms and template-driven forms?
- **Reactive Forms**: Defined programmatically in the component; more scalable and testable
- **Template-Driven Forms**: Defined in the template; simpler for small forms

### How do you perform form validation in Angular?
**Reactive Forms**:
```typescript
this.myForm = new FormGroup({
  name: new FormControl('', [Validators.required, Validators.minLength(3)])
});
```

**Template-Driven Forms**:
```html
<input name="name" ngModel required minlength="3" />
```

### How do you bind form data to the component?
- **Reactive Forms**: Use FormGroup and FormControl bindings
- **Template-Driven Forms**: Use [(ngModel)]="property" for two-way binding

## HTTP and Observables

### How do you make HTTP requests in Angular?
Use HttpClient module:
```typescript
this.http.get('api/url').subscribe(data => console.log(data));
```

### What is the purpose of the HttpClient module?
Simplifies HTTP requests and handles tasks like request headers, responses, and error handling with Observable support.

### What is an observable, and how is it used in Angular?
Observables are streams of data that can emit multiple values over time. Angular uses them for asynchronous operations like HTTP calls and events.

### What is the difference between Promise and Observable?
- **Promise**: Emits a single value and is not cancellable
- **Observable**: Can emit multiple values, is cancellable, and supports operators like map and filter

## Angular Modules

### What is the purpose of NgModules?
NgModules group components, directives, pipes, and services into cohesive blocks to organize an Angular application.

### Explain the difference between feature modules and shared modules.
- **Feature Modules**: Contain components and services specific to a feature
- **Shared Modules**: Contain reusable components, pipes, and directives

### How do you organize an Angular application into modules?
Create feature modules for individual functionalities, a shared module for reusable code, and core modules for singleton services.

## Performance and Optimization

### What is AOT (Ahead-of-Time) compilation, and why is it important?
AOT compiles Angular HTML and TypeScript into JavaScript at build time, reducing runtime overhead and improving performance.

### How does Angular handle tree shaking?
Tree shaking removes unused modules and code during the build process, reducing bundle size.

### What are some ways to optimize an Angular application?
- Use lazy loading for routes
- Minimize change detection with OnPush
- Optimize template bindings
- Enable AOT compilation
- Use lightweight libraries

## Miscellaneous

### What are Angular Pipes? How do you create a custom pipe?
Pipes transform data in templates. Create a custom pipe:
```typescript
@Pipe({ name: 'customPipe' })
export class CustomPipe implements PipeTransform {
  transform(value: string): string {
    return value.toUpperCase();
  }
}
```

### What is the difference between Angular's ngOnInit and constructor?
- **Constructor**: Used for dependency injection
- **ngOnInit**: Executes after component initialization; ideal for initialization logic

### What is the purpose of Angular's zone.js?
zone.js intercepts and tracks asynchronous tasks, enabling Angular's change detection.

### What are interceptors, and how are they used in Angular?
Interceptors intercept HTTP requests/responses for tasks like adding headers or handling errors:
```typescript
@Injectable()
export class AuthInterceptor implements HttpInterceptor {
  intercept(req: HttpRequest<any>, next: HttpHandler) {
    const authReq = req.clone({ setHeaders: { Authorization: 'Bearer token' } });
    return next.handle(authReq);
  }
}
```

### Explain the role of Change Detection in Angular.
Change detection updates the DOM when data changes in the component:
- **Default**: Checks the entire component tree
- **OnPush**: Only checks when input properties change

### What is the role of the trackBy function in ngFor?
Optimizes rendering by tracking items using a unique identifier to prevent unnecessary DOM updates.

## Advanced Concepts

### Architecture and Best Practices

#### How do you design a scalable Angular application architecture?
- Use modular architecture with feature modules
- Implement shared modules for reusable components
- Apply lazy loading for optimizing large-scale applications
- Follow SOLID principles for component and service design

#### How do you handle state management in Angular applications?
- Use libraries like NgRx, Akita, or services with BehaviorSubjects
- Implement NgRx for complex applications with features like selectors, effects, and reducers
- Use OnPush change detection strategy for performance
- Ensure immutability with libraries like immer or plain JavaScript techniques

### Testing

#### How do you ensure robust testing for Angular applications?
- Write unit tests using Jasmine and Karma for components, services, and pipes
- Write integration tests using Angular Testing Utilities like TestBed
- Use end-to-end (E2E) testing with Protractor or Cypress
- Mock dependencies using libraries like Jest or Angular's testing utilities

#### What strategies do you use for mocking HTTP requests in tests?
```typescript
it('should fetch data', () => {
  service.getData().subscribe(data => {
    expect(data).toEqual(mockData);
  });
  const req = httpTestingController.expectOne('api/data');
  req.flush(mockData);
});
```

## Real-World Challenges

### How do you handle application security in Angular?
- Sanitize user inputs with Angular's DomSanitizer
- Avoid cross-site scripting (XSS) by using Angular's template bindings
- Use Angular's built-in CSRF protection
- Secure HTTP calls with HTTPS and authentication tokens

### How do you handle version upgrades in large Angular projects?
- Use Angular Update Guide for a step-by-step upgrade plan
- Upgrade Angular CLI and dependencies incrementally
- Run unit tests and e2e tests after each upgrade
- Refactor deprecated APIs gradually


## What are the major updates in Angular 19?
The major updates done in the Angular 19 are:

- Standalone Components: In Angular 19, components, directives, and pipes are standalone by default, making development easier and reducing reliance on NgModules. The ng update command helps migrate older projects.
Improved Rendering: Angular now supports incremental hydration (still in preview), offering better control over when and how parts of the application are rendered, enhancing performance.
- Route-Level Render Mode: Developers can customize rendering strategies for different routes to improve performance and SEO.
State Management & Async Enhancements: New features like linked signals and the resource API improve state management and make handling asynchronous operations smoother.
- Code and Performance Improvements: Updates like automatic detection of unused imports, Hot Module Replacement (HMR), zoneless change detection (in development), automatic CSP generation, and Angular Material enhancements help streamline development and improve performance.

## What is Difference between Angular 18 and Angular 19?
- Angular 19 offers better performance, easier component management, and improved features for developers.

Feature

Angular 18

Angular 19

Standalone Components

Components still need NgModules.

Components are standalone by default, no need for NgModules.

Routing and SEO

Basic routing optimizations.

Different routes can have different rendering methods, improving performance and SEO.

Performance

Improved performance but limited control.

More control over app rendering for better performance (like Incremental Hydration).

State Management

Basic state management tools.

New tools (Linked Signals, Resource API) for better managing async operations.

Unused Imports

You need to check and remove unused imports manually.

Automatically finds and reports unused imports.

## Why Angular was introduced?
- Angular was introduced to simplify the development of dynamic, single-page applications (SPAs). It offers features like two-way data binding, component-based architecture, and dependency injection, making it easier to manage large applications. Angular also supports cross-platform development, improving code maintainability, performance, and reducing development time for web, mobile, and desktop apps.

## How many types of compilation Angular provides?
Angular provides two types of compilation:

JIT (Just-in-Time) Compilation:

Happens at runtime in the browser.
Compiles the Angular application in the browser as it loads.
Faster development builds but slower performance in production.
AOT (Ahead-of-Time) Compilation:

Happens during the build phase before the application is run.
Compiles the application into efficient JavaScript code ahead of time, which leads to faster loading and better performance.
Recommended for production builds.
In JIT compilation, the application compiles inside the browser during runtime. 
AOT compilation, the application compiles during the build time.

## What is a component in Angular?
- A component is a fundamental building block of Angular applications. It controls a part of the user interface and manages the data and logic for that section. Components are used to create reusable UI elements and define the structure and behavior of the app.

```
import { Component, Input } from '@angular/core';

@Component({
    selector: 'app-header',
    templateUrl: './header.component.html',
    styleUrls: ['./header.component.css']
})
export class HeaderComponent {
    @Input() title: string;
    @Input() links: { name: string, url: string }[];

    constructor() { }
}
```

## Explain the purpose of @Component decorator in Angular.
- Defining the Component: It designates a class as an Angular component and provides metadata about the component.
- Template Association: Links the component with its HTML template, defining the view.
- Style Binding: Associates the component with its CSS styles to encapsulate and manage styling.
Selector Definition: Defines a custom HTML tag (selector) that represents the component in the application.
-Dependency Injection Configuration: Specifies the providers for the component, providing dependency injection.

---


# Angular Interview Questions

A comprehensive collection of Angular interview questions and answers for beginners, intermediate, and experienced developers.

## Table of Contents

- [Basic Angular Interview Questions](#basic-angular-interview-questions)
- [Intermediate Angular Interview Questions](#intermediate-angular-interview-questions)
- [Angular Interview Questions For Experienced](#angular-interview-questions-for-experienced)
- [Angular Scenario Based Interview Questions](#angular-scenario-based-interview-questions)

## Basic Angular Interview Questions

### 15. What are Angular Lifecycle Hooks?
Angular lifecycle hooks are methods that allow developers to tap into key moments in a component's lifecycle. Key hooks include ngOnInit (called once when the component is initialized), ngOnChanges (called when input properties change), and ngOnDestroy (called before Angular destroys the component).

### 16. What is the difference between Angular and AngularJS?

| Feature | Angular | AngularJS |
|---------|---------|-----------|
| Architecture | Component-based architecture | MVC (Model-View-Controller) |
| Language | TypeScript | JavaScript |
| Mobile Support | Designed with mobile support | Limited mobile support |
| Performance | Higher performance with AOT compilation | Relatively slower due to dynamic compilation |
| Data Binding | Two-way data binding with reactive forms and observables | Two-way data binding with scopes and watchers |

### 17. What Data Binding in AngularJS?
Data Binding in Angular provides a function Data Binding which helps us to have an almost real-time reflection of the input given by the user i.e. it creates a connection between Model and View.

### 18. Differences between one-way binding and two-way binding

| Features | One-Way Binding | Two-Way Binding |
|----------|----------------|----------------|
| Definition | Data flows in one direction (from component to view or vice versa). | Data flows in both directions (from component to view and vice versa). |
| Data Flow | Unidirectional (either component → view or view → component). | Bidirectional (component ↔ view). |
| Complexity | Simpler to implement as it handles data in one direction only. | More complex, as it involves synchronization between the view and the component. |
| Use Case | Used when the view only needs to display data or when the component updates based on view changes. | Used when you want to reflect changes in the model immediately to the view and vice versa. |
| Example | {{ message }} or [property]="value" | [(ngModel)]="value" |

### 19. What is string interpolation in AngularJS?
String interpolation is a technique used to bind data from the model (JavaScript) to the view (HTML) by embedding expressions within double curly braces {{ }}. It allows you to insert dynamic values or variables into the HTML content, making the view update automatically when the model changes.

```html
<div>{{ message }}</div>
```

### 20. How many types of Directives are available in AngularJS?
There are four kinds of directives in AngularJS:
- Element directives
- Attribute directives
- CSS class directives
- Comment directives

### 21. What is factory method in AngularJS?
AngularJS Factory Method makes the development process of AngularJS application more robust. A factory is a simple function that allows us to add some logic to a created object and return the created object.

- The factory is also used to create/return a function in the form of reusable code which can be used anywhere within the application.
- Whenever we create an object using a factory it always returns a new instance for that object.
- The object returned by the factory can be integrated(injectible) with different components of the Angularjs framework such as controller, service, filter or directive.

### 22. What is the digest cycle in AngularJS?
The digest cycle in AngularJS is a process where Angular compares the current and previous values of the scope model to check for changes. If changes are detected, Angular updates the view. This cycle is triggered automatically after an event like a user action, HTTP request, or model change, and it ensures that the view stays in sync with the model. It can also be manually triggered using $apply().

### 23. What is dependency injection in Angular?
Dependency Injection (DI) in Angular is a design pattern where services or objects are provided to components or other services rather than being created within them. It allows for better modularity, testability, and management of dependencies. Angular's DI framework automatically injects required services into components, making it easier to manage and maintain the application.

### 24. How do you create a service in Angular?
A service can be created using Angular CLI or manually by creating a class decorated with @Injectable().

Creating a data fetching service:

```typescript
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable({
    providedIn: 'root'
})
export class DataFetchingService {
    private apiUrl = 'https://api.example.com/data'; 

    constructor(private http: HttpClient) { }

    fetchData(): Observable<any> {
        return this.http.get<any>(this.apiUrl);
    }
}
```

### 25. What is an Angular router?
The Angular router is a library that enables navigation between different views or pages in a single-page application (SPA). It allows developers to define routes, handle URL changes, and load components dynamically based on the route, providing a smooth and efficient user experience without page reloads.

### 26. What is scope in Angular?
In Angular, scope refers to the environment or context in which variables, expressions, and functions are evaluated. It determines the visibility and accessibility of these variables within different parts of the application, particularly in relation to the component's template and controller.

Note: In Angular 2+ (modern Angular), the term scope is no longer used. It is replaced by component state and data binding.

## Intermediate Angular Interview Questions

### 27. What type of DOM is used in Angular?
Angular uses the Real DOM (Document Object Model). The Change Detection mechanism is used to update only the affected parts of the DOM when data changes, improving performance. In addition, Angular uses a Shadow DOM for encapsulation, which helps isolate styles and behavior of components.

- Real DOM: Updates the entire DOM when changes occur.
- Change Detection: Optimizes updates to only parts of the DOM that need re-rendering.
- Shadow DOM: Provides component style and behavior encapsulation.

### In How many ways Bootstrap is embedded in Angular?
In Angular, bootstrap can be implemented by two ways:

1. Using npm (Recommended): Install Bootstrap via npm and import it into the angular.json file under the "styles" and "scripts" arrays.
```
npm install bootstrap
```

2. Using CDN (Content Delivery Network): Instead of installing Bootstrap locally, you can link to Bootstrap's CSS and JS files directly from a CDN in your index.html file:
```html
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.16.0/umd/popper.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
```

### 28. How can you pass data between components in Angular?
Data can be passed between components using Input and Output decorators, services, or router state.

Passing data from a parent component to a child component using @Input decorator:

```typescript
//child.component.ts
import { Component, Input } from '@angular/core';

@Component({
    selector: 'app-child',
    templateUrl: './child.component.html',
    styleUrls: ['./child.component.css']
})
export class ChildComponent {
    @Input() childData: string; // Declare the input property
}

//Child.component.html
<div>
    <p>Data from parent: {{ childData }}</p>
</div>

//parent.component.ts
import { Component } from '@angular/core';

@Component({
    selector: 'app-parent',
    templateUrl: './parent.component.html',
    styleUrls: ['./parent.component.css']
})
export class ParentComponent {
    parentData: string = 'Hello from Parent Component!';
}

//parent.component.html
<div>
    <app-child [childData]="parentData"></app-child>
</div>

//App.module.ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';
import { ParentComponent } from './parent/parent.component';
import { ChildComponent } from './child/child.component';

@NgModule({
    declarations: [
        AppComponent,
        ParentComponent,
        ChildComponent
    ],
    imports: [
        BrowserModule
    ],
    providers: [],
    bootstrap: [AppComponent]
})
export class AppModule { }
```

### 29. Explain lazy loading in Angular.
Lazy loading in Angular is a technique used to improve the performance of an application by loading feature modules only when they are needed, rather than loading all modules upfront. This reduces the initial load time of the application and speeds up the startup process.

### 30. What is MVVM architecture in Angular?
MVVM (Model-View-ViewModel) is a software architectural pattern that is commonly used in Angular applications, providing a clean separation of concerns between different components of an application. This ensures that changes in one part of the application (like in the logic or data) do not directly affect or interfere with the user interface.

Here's how MVVM works in Angular:

**Model:**
- Represents the application's data and logic.
- It is the part of the application that manages the state, and it can be composed of services, APIs, or even simple objects.
- In Angular, the Model can be represented by services or interfaces that fetch data from a database or API and expose methods for interacting with that data.

**View:**
- Represents the UI (user interface) elements that the user interacts with, such as buttons, inputs, forms, etc.
- In Angular, the View is typically defined using HTML and CSS, and it's tied to the template of a component.
- The view listens for changes in the ViewModel and displays updated data to the user.

**ViewModel:**
- This is the key part of MVVM in Angular. It acts as a bridge between the Model and View.
- The ViewModel holds the data and logic needed to present the Model's data in a way that the View can easily display.
- It is represented by the component in Angular, which binds the data and defines the behavior that will be reflected in the view.
- Angular's two-way data binding (via ngModel) allows the ViewModel to automatically synchronize with the View, enabling automatic updates when data changes.

### 31. What are Angular lifecycle hooks?
Angular lifecycle hooks are methods that allow you to tap into key moments in a component's lifecycle. Here are the main lifecycle hooks:

- ngOnInit(): Called once after the component's data-bound properties have been initialized.
- ngOnChanges(changes: SimpleChanges): Called whenever one or more data-bound input properties change.
- ngDoCheck(): Called during every change detection run, allowing you to implement your own change detection.
- ngAfterContentInit(): Called once after Angular projects external content into the component's view.
- ngAfterContentChecked(): Called after every check of projected content.
- ngAfterViewInit(): Called once after the component's view (and child views) has been initialized.
- ngAfterViewChecked(): Called after every check of the component's view (and child views).
- ngOnDestroy(): Called just before Angular destroys the component, allowing you to clean up resources.

### 32. What is a pipe in Angular?
A pipe is a way to transform data in the template. It allows you to format or manipulate data before displaying it to the user. Angular provides several built-in pipes like DatePipe, UpperCasePipe, and CurrencyPipe, and you can also create custom pipes. Pipes are typically used to modify the display of data without altering the original data itself.

### 33. What is Angular Universal?
Angular Universal is a technology that enables server-side rendering (SSR) for Angular applications, improving performance, initial load times, and search engine optimization (SEO) by pre-rendering the application on the server before sending it to the client. This results in faster, more interactive user experiences and better indexing by search engines.

### 34. How do you optimize Angular applications?
To optimize Angular applications, you can:

- Use AOT (Ahead-of-Time) Compilation: Pre-compile the application to improve startup time and reduce the size of the bundle.
- Lazy Loading: Load modules only when they are needed to reduce initial loading time.
- OnPush Change Detection: Use the OnPush change detection strategy to minimize unnecessary checks.
- Tree Shaking: Remove unused code during the build process to reduce bundle size.
- Minification and Uglification: Minify and compress JavaScript and CSS files for smaller payloads.
- Use TrackBy with ngFor: Improve performance in lists by using trackBy to avoid re-rendering unchanged items.
- Service Workers: Implement service workers for caching and offline support.

### 35. What are Angular interceptors?
Angular interceptors are services that intercept and modify HTTP requests and responses. They allow you to perform actions such as adding headers (e.g., authentication tokens), logging, or handling errors globally. Interceptors are useful for managing HTTP communication centrally in Angular applications.

### 36. Explain the purpose of NgZone in Angular.
NgZone in Angular is a service that helps Angular know when to update the view by tracking asynchronous operations. It runs change detection whenever an asynchronous operation, like a setTimeout or HTTP request, completes. NgZone ensures that Angular is aware of changes in the application state and triggers the necessary updates to the view.

### 37. What is the difference between @Input() and @Output() in Angular?

| Decorator | Purpose | Example |
|-----------|---------|---------|
| @Input() | Pass data from parent to child component | <child [childData]="parentData"></child> |
| @Output() | Emit events from child to parent component | <child (childEvent)="parentMethod($event)"></child> |

### 38. How do you implement authentication in Angular?
Authentication can be implemented using JWT tokens, Angular guards, and interceptors to manage login and secure routes.

Securing a route with an AuthGuard:

```typescript
import { Injectable } from '@angular/core';

@Injectable({
    providedIn: 'root'
})
export class AuthService {

    constructor() { }

    isLoggedIn(): boolean {
        return !!localStorage.getItem('userToken');
    }
}
```

### 39. What are Standalone Components in Angular 19?
In Angular 19, Standalone Components continue to offer significant advantages. They are components that do not rely on NgModules to function, simplifying Angular application architecture. This reduces the need for complex module dependencies and enhances tree-shaking for better optimization. Standalone components allow for more independent and modular development, making it easier to manage, test, and reuse components without requiring an entire NgModule setup. They contribute to cleaner code, better performance, and a more flexible development workflow, further streamlining Angular applications.

### 40. How do you use Typed Forms?
Typed Forms continue to provide enhanced type safety for reactive forms. You can define strict types for form controls using FormGroup, FormControl, and FormArray, ensuring better type-checking and preventing runtime errors. This approach allows for more robust form handling, as you can specify the exact types for form values, leading to improved developer experience and better maintainability. The type-safe reactive forms in Angular 19 ensure consistency, making it easier to manage form controls and access their values with proper type support.

### 41. What is the purpose of the Signal API?
The Signal API is a key tool in simplifying state management, making Angular applications more responsive and efficient. Signal API has evolved to provide more efficient tracking of reactive state changes and dependencies. It helps in managing data flow by introducing reactive signals, which automatically detect changes in state and update the view without requiring manual change detection. This reduces the complexity of handling reactivity and optimizes performance by minimizing unnecessary updates.

### 42. How does the inject() function work?
The inject() function simplifies the process of dependency injection (DI). It allows developers to access and inject services or dependencies directly within the component's constructor or lifecycle methods without the need for constructor injection.

### 43. What improvements have been made to standalone testing?
Standalone components can now be tested directly, reducing boilerplate code and enhancing tree-shaking by avoiding unnecessary module dependencies. The testing framework has been optimized for better performance and developer experience. Angular 19 also improves integration with testing libraries like Jasmine and Karma, allowing for more straightforward configuration, faster tests, and a smoother testing process.

### 44. Explain the use of Functional Components.
Functional components focus purely on rendering UI based on inputs and outputs, without requiring a class structure. This approach brings a more functional programming style to Angular, making it easier to write and test components with better performance, especially for simple and reusable components.

### 45. What is Ahead-of-Time (AOT) compilation in Angular?
Ahead-of-Time (AOT) compilation in Angular is the process of compiling Angular templates and TypeScript code into efficient JavaScript code during the build process, before the application is run in the browser. This reduces the size of the application, improves startup performance, and allows for earlier detection of template errors, resulting in faster rendering and better overall performance in production.

### 46. What is Ivy in Angular?
Ivy is Angular's next-generation rendering engine, introduced to improve performance and reduce bundle sizes. It offers faster compilation, more efficient rendering, and enhanced debugging capabilities. Ivy's advanced tree-shaking features eliminate unused code, leading to smaller and faster applications. Additionally, Ivy provides better backward compatibility, making it easier to update and maintain Angular applications.

### 47. Explain the purpose of Angular Elements.
- Web Component Integration: Allows Angular components to be packaged as custom elements (web components) that can be used in any HTML page or framework.
- Reusability: Enables the reuse of Angular components across different projects and frameworks, providing code sharing and consistency.
- Interoperability: Provides the integration of Angular components into non-Angular applications, enhancing flexibility and compatibility.
- Encapsulation: Provides encapsulated, self-contained components that encapsulate their logic, styles, and templates, reducing the risk of conflicts in larger applications.

### 48. What is a Resolver in Angular?
A Resolver in Angular is a service that pre-fetches data before a route is activated, ensuring that the necessary data is available when the route is accessed. This is particularly useful for loading important data that a component depends on, thereby enhancing user experience by avoiding loading indicators or incomplete views.

## Angular Interview Questions For Experienced

### 49. What is difference between Angular and React?

| Feature | Angular | React |
|---------|---------|-------|
| Type | Full-fledged framework | Library for building user interfaces |
| Developed by | Google | Facebook |
| Language | TypeScript (JavaScript superset) | JavaScript (JSX syntax) |
| Architecture | MVC (Model-View-Controller) / MVVM (Model-View-ViewModel) | Component-based architecture |
| Use Case | Suitable for large-scale applications with complex requirements | Best for building interactive UIs and SPAs (Single Page Applications) |

### 50. How are Angular expressions are different from JavaScript expressions?
Angular Expressions are a simplified version of JavaScript expressions designed for use within templates and for data binding, while JavaScript Expressions are more flexible and can be used to perform various operations in the logic layer of an application.

### 51. What is the purpose of NgModule in Angular?
The purpose of NgModule in Angular is to organize an application into cohesive blocks of functionality by grouping related components, directives, pipes, and services. NgModule defines a compilation context for these elements, providing modularity and maintainability.

### 52. What is the difference between Template-driven and Reactive Forms?

| Feature | Template-driven Forms | Reactive Forms |
|---------|----------------------|----------------|
| Structure | Based on directives | Based on explicit creation |
| Validation | Asynchronous | Synchronous |
| Complexity | Simple forms | Complex forms |
| Data Model | Two-way data binding | Immutable data model |

### 53. What are Angular Guards?
Angular Guards are services that control access to routes in an Angular application. They are used to protect routes from unauthorized access or to prevent unwanted navigation. Common types of guards include:

- CanActivate: Determines if a route can be activated.
- CanDeactivate: Checks if a route can be deactivated.
- CanLoad: Determines if a module can be loaded lazily.

### 54. How do you create custom validators in Angular?
Custom validators can be created by implementing the ValidatorFn interface and using it in the form controls.

Creating a custom validator to check if a username is available:

```typescript
import { AbstractControl, ValidationErrors, ValidatorFn } from '@angular/forms';
import { Injectable } from '@angular/core';
import { Observable, of } from 'rxjs';
import { map } from 'rxjs/operators';

@Injectable({
    providedIn: 'root'
})
export class UsernameValidatorService {
    private takenUsernames = ['admin', 'user', 'guest'];

    checkUsername(username: string): Observable<boolean> {
        return of(this.takenUsernames.includes(username)).pipe(
            map(isTaken => !isTaken)
        );
    }
}
```

### 55. What is the purpose of Angular animations?
The purpose of Angular animations is to add dynamic visual effects to applications, improving user experience by making transitions, state changes, and movements more engaging. They enable smooth animations for elements such as fading, sliding, or resizing, triggered by user interactions or state changes in the application.

### 56. Explain dynamic components in Angular.
Dynamic components in Angular are components that are created and inserted into the application at runtime, rather than being statically declared in the template. This allows for greater flexibility and responsiveness in applications.

### 57. What is Angular Material?
Angular Material is a UI component library for Angular applications that provides pre-built, reusable, and customizable user interface components, following Google's Material Design principles. It offers components like buttons, dialogs, form controls, and navigation elements, helping developers create modern, responsive, and visually appealing applications quickly.

### 58. What is Eager?
In AngularJS, eager loading refers to the process where modules, services, and controllers are loaded at the start of the application, even if they are not immediately needed. Eager loading is typically used when the developer expects all parts of the application to be used early on.

### 59. What is the purpose of Angular's Renderer2?
- Platform Agnostic: Renderer2 provides a platform-agnostic way to manipulate the DOM, ensuring that the application can run consistently across different environments, such as server-side rendering with Angular Universal or web workers.
- Security: It helps prevent XSS (Cross-Site Scripting) attacks by sanitizing inputs and ensuring safe interactions with the DOM.
- Abstraction: Renderer2 abstracts away direct DOM manipulation, making the code more testable and maintainable by allowing developers to focus on logical rather than low-level DOM operations.
- Consistency: Ensures consistent behavior across various browsers and platforms.

### 60. What is the difference between AOT and JIT?

| Feature | AOT (Ahead-of-Time) Compilation | JIT (Just-in-Time) Compilation |
|---------|--------------------------------|-------------------------------|
| Compilation Time | Compilation occurs at build time | Compilation occurs at runtime |
| Performance | Faster startup time, as the code is already compiled | Slower startup time, as the code is compiled in the browser |
| Error Detection | Errors are detected at build time, allowing for earlier fixes | Errors are detected at runtime, which may affect the user experience |
| Bundle Size | Smaller bundle size, as the compiler is not included in the bundle | Larger bundle size, as the compiler is included in the bundle |
| Compatibility | Better suited for production environments, including server-side rendering | Often used in development environments for faster iteration and debugging |

### 61. What are the benefits of using Web Workers in Angular?
- Improved Performance: Web Workers allow for offloading heavy computations and tasks to background threads, freeing up the main thread and ensuring smoother and more responsive user interfaces.
- Enhanced User Experience: By running complex operations in the background, Web Workers prevent the UI from becoming unresponsive, providing a seamless and uninterrupted user experience.
- Parallel Processing: Web Workers enable parallel processing of tasks, which can significantly speed up operations that are computationally intensive or involve large datasets.
- Better Scalability: Utilizing Web Workers can help scale applications more effectively by distributing the workload, leading to more efficient resource utilization and improved performance under high load conditions.

### 62. What is Data Binding in Angular?
Data binding in Angular is a mechanism that allows communication between the component and the view (HTML template). It synchronizes the data between the model (component) and the view, making it easy to reflect changes in the UI whenever data changes in the component.

There are 4 types of data binding in Angular:

1. Interpolation (One-way Binding)
2. Property Binding (One-way Binding)
3. Event Binding (One-way Binding)
4. Two-way Binding

### 63. What are impure pipes in angular?
Impure pipes in Angular are pipes that can change the output when input values change over time, even without the change detection running. Unlike pure pipes, impure pipes are evaluated every time change detection runs, which can lead to performance issues if not used carefully.

### 64. What are pure pipes in angular?
Pure pipes in Angular are pipes that only re-evaluate when their input data changes. This makes them more efficient compared to impure pipes, as they are only executed when the values of the inputs change.

### 65. What is Pipe transform Interface in Angular?
In Angular, the PipeTransform interface is used to define the structure of a custom pipe. It is part of the Pipe decorator, which helps in creating custom pipes to transform data within templates.

## Angular Scenario Based Interview Questions

### 66. Scenario: Handling Data from Multiple APIs
**Question:** We are developing an Angular application that needs to fetch data from multiple APIs and display them together on the same page. How would we handle asynchronous API calls and ensure the data is displayed after all responses are received?

**Answer:** I would use the RxJS forkJoin operator to handle multiple API calls concurrently. This ensures that all API responses are received before processing the data. Here's how I would implement it:

```typescript
import { forkJoin } from 'rxjs';
import { HttpClient } from '@angular/common/http';

constructor(private http: HttpClient) { }

getData() {
    const api1$ = this.http.get('https://api1.example.com');
    const api2$ = this.http.get('https://api2.example.com');

    forkJoin([api1$, api2$]).subscribe(
        ([api1Response, api2Response]) => {
            // Process data from both APIs
            this.processData(api1Response, api2Response);
        },
        error => {
            console.error('Error fetching data', error);
        }
    );
}
```

forkJoin waits until all observables complete and then emits the results in an array. This is perfect for scenarios where you want to fetch data from multiple sources simultaneously.

### 67. Scenario: Optimizing Angular Performance with Lazy Loading
**Question:** Your Angular application is getting slower due to a large number of modules and components. How would you optimize the application's performance?

**Answer:** One way to optimize an Angular application is by implementing lazy loading to load modules only when needed. This reduces the initial bundle size, improving load times. Here's an example of setting up lazy loading in Angular:

```typescript
// app-routing.module.ts
const routes: Routes = [
    { path: 'feature', loadChildren: () => import('./feature/feature.module').then(m => m.FeatureModule) }
];
```

By using the loadChildren property, Angular will load the FeatureModule only when the user navigates to the /feature route. This improves the app's performance by deferring the loading of non-essential modules.

### 68. Scenario: Handling Form Validation in Reactive Forms
**Question:** We have a form where the user enters their email, and we need to ensure that it is both valid and unique (not already in use). How would we implement this validation using Angular Reactive Forms?

**Answer:** I would use Reactive Forms with custom synchronous and asynchronous validators. Here's how I would implement both email format validation and uniqueness check:

```typescript
import { FormBuilder, FormGroup, Validators } from '@angular/forms';
import { of } from 'rxjs';
import { map, delay } from 'rxjs/operators';

constructor(private fb: FormBuilder) { }

emailForm: FormGroup = this.fb.group({
    email: ['', [Validators.required, Validators.email], [this.uniqueEmailValidator.bind(this)]]
});

uniqueEmailValidator(control: AbstractControl) {
    const emailsInUse = ['test@example.com', 'user@example.com'];
    return of(emailsInUse.includes(control.value)).pipe(
        delay(500),
        map(isInUse => (isInUse ? { emailInUse: true } : null))
    );
}
```

The Validators.email ensures the entered email is valid, while the uniqueEmailValidator checks asynchronously whether the email is already in use. If so, it returns an error, otherwise, it passes validation.

### 69. Scenario: Debugging Change Detection Issues
**Question:** We notice that a component is not updating as expected when data changes. How would you debug and resolve the issue related to Angular's change detection mechanism?

**Answer:** First, I would check if the component is using OnPush change detection strategy:

```typescript
@Component({
  selector: 'app-sample',
  templateUrl: './sample.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush
})
```

If the OnPush strategy is being used, Angular only checks for changes when an input reference changes. If the data is updated by mutation, Angular will not detect the change. In this case, I would either:

```typescript
constructor(private cd: ChangeDetectorRef) {}

updateData() {
    this.data = { ...this.data, newValue: 'updated' };
    this.cd.markForCheck();  
}
```

If the object is mutated directly, OnPush doesn't detect the change. Ensure the object reference is changed, or manually trigger change detection using ChangeDetectorRef. Creating a new object or using markForCheck ensures that Angular runs change detection.

### 70. Scenario: Implementing Route Guards for Authentication
**Question:** How would you protect specific routes in your Angular application so that only authenticated users can access them?

**Answer:** I would implement Route Guards using Angular's CanActivate interface to protect routes. Here's an example of how to implement an authentication guard:

```typescript
import { Injectable } from '@angular/core';
import { CanActivate, Router } from '@angular/router';
import { AuthService } from './auth.service';

@Injectable({
    providedIn: 'root'
})
export class AuthGuard implements CanActivate {

    constructor(private authService: AuthService, private router: Router) { }

    canActivate(): boolean {
        if (this.authService.isAuthenticated()) {
            return true;
        } else {
            this.router.navigate(['/login']);
            return false;
        }
    }
}
```

The AuthGuard checks if the user is authenticated before allowing access to the route. If the user is not authenticated, they are redirected to the login page. This ensures that only authorized users can access certain parts of the application.


## 📚 Additional Resources

- [Angular Official Documentation](https://angular.io/docs)
- [Angular CLI Overview](https://angular.io/cli)
- [Angular GitHub Repository](https://github.com/angular/angular)

---
