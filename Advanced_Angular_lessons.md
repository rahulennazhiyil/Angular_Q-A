Mastering Angular Structural Elements and Directives
----------------------------------------------------
Angular is a powerful framework that offers various tools to enhance the UI and manage the DOM effectively. In this blog, we will cover the following concepts in detail with beginner-friendly examples and outputs:

* ng-template
* ng-container
* ng-content
* ElementRef
* TemplateRef
* ViewContainerRef
* ngTemplateOutlet
* Custom Directives
* Renderer2
* Structural Directives (*ngIf, *ngFor, etc.)

1. ng-template
--------------
The ng-template directive is used to define a reusable and non-rendered block of HTML until explicitly invoked. It is highly versatile and works with structural directives, custom directives, and dynamic content rendering. It is also instrumental in creating reusable components.

Advanced Use Cases
1. Using ng-template with ngIf
You can define templates for conditional rendering directly within an ngIf directive.

<div *ngIf="isLoggedIn; else loginTemplate">
  <p>Welcome back, user!</p>
</div>

<ng-template #loginTemplate>
  <p>Please log in to continue.</p>
</ng-template>

2. Reusable Components
----------------------
ng-template allows for content reuse in dynamic components. Here's an example:

Parent Component:

<app-message [template]="customTemplate"></app-message>

<ng-template #customTemplate>
  <p>Custom message content!</p>
</ng-template>
Child Component:

<div>
  <ng-container *ngTemplateOutlet="template"></ng-container>
</div>
Component Code:

import { Component, Input, TemplateRef } from '@angular/core';

@Component({
  selector: 'app-message',
  templateUrl: './message.component.html',
})
export class MessageComponent {
  @Input() template!: TemplateRef<any>;
}

3. Dynamic Context Passing
--------------------------
With ngTemplateOutletContext, you can pass data dynamically to templates, enabling more flexible logic.

<ng-template #greeting let-name="name">
  <p>Hello, {{ name }}!</p>
</ng-template>

<ng-container *ngTemplateOutlet="greeting; context: { name: 'Angular Developer' }"></ng-container>

4. Usage in Custom Directives
-----------------------------
You can combine ng-template with custom structural directives to create powerful DOM transformations. For instance, rendering templates conditionally:

import { Directive, Input, TemplateRef, ViewContainerRef } from '@angular/core';

@Directive({
  selector: '[appCustomRender]',
})
export class CustomRenderDirective {
  @Input() set appCustomRender(condition: boolean) {
    if (condition) {
      this.vcr.createEmbeddedView(this.templateRef);
    } else {
      this.vcr.clear();
    }
  }

  constructor(private templateRef: TemplateRef<any>, private vcr: ViewContainerRef) {}
}
Usage:

<ng-template [appCustomRender]="isActive">
  <p>Active Content Rendered!</p>
</ng-template>
Summary
ng-template is an essential tool in Angular for defining reusable, dynamic, and efficient templates. By leveraging its advanced capabilities, you can create robust and modular components in your Angular applications. ng-template directive is used to define a reusable and non-rendered block of HTML until explicitly invoked. It is highly versatile and works with structural directives and dynamic content rendering.

Use Cases
Conditional rendering using *ngIf.
Storing reusable template code.
Dynamic content rendering with ngTemplateOutlet.
Placeholder content.
Creating dynamic components in reusable modules.
Example
<ng-template>
  <p>This content is rendered using ng-template!</p>
</ng-template>

<!-- Usage of ng-template -->
<div *ngIf="showContent; else noContent">
  <p>Content is shown!</p>
</div>

<ng-template #noContent>
  <p>No content to show!</p>
</ng-template>
Component Code
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
})
export class AppComponent {
  showContent = false;
}
Output
When showContent is false:

No content to show!
When showContent is true:

Content is shown!

2. ng-container
---------------
The ng-container is a grouping element that doesn't render an additional DOM element. It is used to group elements logically and apply directives without affecting the DOM structure.

Use Cases
Logical grouping of elements for conditional rendering.
Avoid unnecessary wrappers in the DOM.
Using multiple structural directives together.
Creating dynamic tables or grids efficiently.
Example
<ng-container *ngIf="isLoggedIn">
  <p>Welcome, user!</p>
</ng-container>
Component Code
isLoggedIn = true;
Output
Welcome, user!
If isLoggedIn is false, no output is rendered.

3. ng-content
-------------
The ng-content directive is used to project content into a component from its parent. It enables developers to create highly customizable and reusable components.

Use Cases
Content projection in reusable components.
Supporting slot-like behavior in components.
Projecting multiple slots with select attribute.
Implementing dynamic layouts in parent-child components.
Example
<!-- Parent Component -->
<app-card>
  <p>Content to be projected</p>
</app-card>

<!-- Child Component Template -->
<div class="card">
  <ng-content></ng-content>
</div>
Output
<div class="card">
  <p>Content to be projected</p>
</div>

4. ElementRef
-------------
ElementRef is used to directly access and manipulate DOM elements. Use it cautiously, as improper usage can lead to security risks like XSS.

Use Cases
Accessing and modifying native DOM elements.
Direct interaction with element attributes or styles.
Custom directive implementation.
Integrating third-party libraries that require direct DOM manipulation.
Example
import { Component, ElementRef, ViewChild } from '@angular/core';

@Component({
  selector: 'app-root',
  template: '<button #btn>Click me!</button>',
})
export class AppComponent {
  @ViewChild('btn', { static: true }) button!: ElementRef;

  ngAfterViewInit() {
    this.button.nativeElement.style.backgroundColor = 'blue';
  }
}
Output
The button will have a blue background color.

5. TemplateRef
--------------
TemplateRef represents an embedded template. It is used to work with structural directives or programmatically render templates.

Use Cases
Creating dynamic views with ViewContainerRef.
Passing templates as inputs.
Handling reusable template logic.
Using TemplateRef to control rendering logic dynamically.
Example
import { Component, TemplateRef, ViewChild } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <ng-template #tpl>
      <p>Rendered by TemplateRef</p>
    </ng-template>
  `,
})
export class AppComponent {
  @ViewChild('tpl', { static: true }) template!: TemplateRef<any>;

  constructor() {}
}

6. ViewContainerRef
-------------------
ViewContainerRef is used to dynamically insert templates or components into the DOM at runtime.

Use Cases
Dynamically adding or removing components.
Rendering templates programmatically.
Creating reusable content renderers.
Efficiently managing dynamic lists or grids.
Example
import { Component, TemplateRef, ViewChild, ViewContainerRef } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <ng-template #tpl>
      <p>Dynamically rendered content!</p>
    </ng-template>
    <button (click)="render()">Render Content</button>
  `,
})
export class AppComponent {
  @ViewChild('tpl', { static: true }) template!: TemplateRef<any>;

  constructor(private vcr: ViewContainerRef) {}

  render() {
    this.vcr.createEmbeddedView(this.template);
  }
}

7. ngTemplateOutlet
-------------------
ngTemplateOutlet allows you to render an ng-template programmatically. It simplifies template management and reuse, and provides powerful options for passing data to templates dynamically.

Use Cases
Rendering conditional templates.
Reusing predefined templates dynamically.
Passing context to templates.
Simplifying repetitive template logic.
Example: Basic Usage
<ng-template #template1>
  <p>This is Template 1</p>
</ng-template>

<ng-container *ngTemplateOutlet="template1"></ng-container>
Output
This is Template 1
Example: Passing Context Data to Templates
Using ngTemplateOutletContext, you can pass data to an ng-template dynamically.

<ng-template #template2 let-name="name">
  <p>Hello, {{ name }}!</p>
</ng-template>

<ng-container *ngTemplateOutlet="template2; context: { name: 'Angular' }"></ng-container>
Output
Hello, Angular!
Example: Conditional Rendering with Context
<ng-template #loggedIn let-user="user">
  <p>Welcome back, {{ user }}!</p>
</ng-template>

<ng-template #loggedOut>
  <p>Please log in to continue.</p>
</ng-template>

<ng-container *ngTemplateOutlet="isLoggedIn ? loggedIn : loggedOut; context: { user: 'John' }"></ng-container>
Component Code
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
})
export class AppComponent {
  isLoggedIn = true;
}
Output
If isLoggedIn is true:

Welcome back, John!
If isLoggedIn is false:

Please log in to continue.

allows you to render an ng-template programmatically. It simplifies template management and reuse.

Use Cases
Rendering conditional templates.
Reusing predefined templates dynamically.
Passing context to templates.
Simplifying repetitive template logic.
Example
<ng-template #template1>
  <p>This is Template 1</p>
</ng-template>

<ng-container *ngTemplateOutlet="template1"></ng-container>
Output
This is Template 1

8. Custom Directives
--------------------
Directives extend the behavior of elements or components. Below is an example of a directive that changes the background color of an element.

Use Cases
Modifying DOM behavior dynamically.
Handling user interactions like hover or click events.
Creating reusable logic encapsulated in directives.
Implementing animation triggers or scroll-based interactions.
Building structural directives to transform the DOM dynamically.
Example: Attribute Directive
import { Directive, ElementRef, Renderer2, HostListener } from '@angular/core';

@Directive({
  selector: '[appHighlight]',
})
export class HighlightDirective {
  constructor(private el: ElementRef, private renderer: Renderer2) {}

  @HostListener('mouseenter') onMouseEnter() {
    this.renderer.setStyle(this.el.nativeElement, 'background-color', 'yellow');
  }

  @HostListener('mouseleave') onMouseLeave() {
    this.renderer.removeStyle(this.el.nativeElement, 'background-color');
  }
}

Usage
<p appHighlight>Hover over me to highlight!</p>
Output
The background of the paragraph changes to yellow when hovered over.

Example: Structural Directive
Structural directives can modify the DOM by adding or removing elements dynamically. Here is an example to toggle visibility based on a condition.

import { Directive, Input, TemplateRef, ViewContainerRef } from '@angular/core';

@Directive({
  selector: '[appIf]',
})
export class IfDirective {
  constructor(private templateRef: TemplateRef<any>, private viewContainer: ViewContainerRef) {}

  @Input() set appIf(condition: boolean) {
    if (condition) {
      this.viewContainer.createEmbeddedView(this.templateRef);
    } else {
      this.viewContainer.clear();
    }
  }
}

Usage
<div *appIf="isVisible">This content is conditionally visible!</div>
Component Code
isVisible = true;

Output
If isVisible is true, the content will be rendered:

This content is conditionally visible!
If isVisible is false, the content will not be displayed. extend the behavior of elements or components. Below is an example of a directive that changes the background color of an element.

Use Cases
Modifying DOM behavior dynamically.
Handling user interactions like hover or click events.
Creating reusable logic encapsulated in directives.
Implementing animation triggers or scroll-based interactions.
Example
import { Directive, ElementRef, Renderer2, HostListener } from '@angular/core';

@Directive({
  selector: '[appHighlight]',
})
export class HighlightDirective {
  constructor(private el: ElementRef, private renderer: Renderer2) {}

  @HostListener('mouseenter') onMouseEnter() {
    this.renderer.setStyle(this.el.nativeElement, 'background-color', 'yellow');
  }

  @HostListener('mouseleave') onMouseLeave() {
    this.renderer.removeStyle(this.el.nativeElement, 'background-color');
  }
}
Usage
<p appHighlight>Hover over me to highlight!</p>
Output
The background of the paragraph changes to yellow when hovered over.

9. Renderer2
------------
Renderer2 is a service used for safely manipulating the DOM. It is a preferred alternative to ElementRef for DOM interactions.

Use Cases
Changing element attributes or styles.
Adding or removing DOM elements dynamically.
Safeguarding against potential XSS attacks.
Example
import { Directive, ElementRef, Renderer2 } from '@angular/core';

@Directive({
  selector: '[appSafeHighlight]',
})
export class SafeHighlightDirective {
  constructor(private el: ElementRef, private renderer: Renderer2) {
    this.renderer.setStyle(this.el.nativeElement, 'border', '1px solid red');
  }
}
Usage
<p appSafeHighlight>This paragraph has a red border.</p>
