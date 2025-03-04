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

---

## 📚 Additional Resources

- [Angular Official Documentation](https://angular.io/docs)
- [Angular CLI Overview](https://angular.io/cli)
- [Angular GitHub Repository](https://github.com/angular/angular)

---
