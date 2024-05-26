---
theme: wordman
class: text-center
highlighter: shiki
lineNumbers: false
info: |

drawings:
  presenterOnly: true
defaults:
  layout: default
title: Pragmatic Typings - Patterns to Reduce Friction and Spark Joy
monaco: false
mdc: true
transition: slide-left
favicon: ./favicon.png
layout: image
image: /title.png
backgroundSize: cover
---
<div class="flex items-center justify-center h-full w-full flex-col">
    <h1 class="text-8xl! text-shadow text-shadow-lg"> Modern Angular</h1>
    <h2 class="text-6xl! text-shadow text-shadow-lg">A Learning Path </h2>
</div>

---
---

# First Commit on Angular Repo
<div class="flex items-center justify-center" style="height: calc(100% - 100px)">
    <img  src="first-commit.png" style="width:65%"/>
</div>

<div v-mark.red.circle class="absolute" style="width: 220px; height: 50px; top: 260px; left:360px"></div>

---
layout: image
image: /angular-rennaisance.png
backgroundSize: cover
---

<h1 class="text-6xl! text-shadow text-shadow-lg" style="bottom: 30px; position: absolute;right: 10px;">Angular Renaissance</h1>

---
layout: image
image: /two-paths.jpeg
backgroundSize: contain
---

---
layout: introduction
---

---
layout: cover
---

# Everything is backwards-compatible as of now! 

---
layout: cover
---

````md magic-move
```angular-ts
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [],
  template: `
    <h1>Default</h1>
  `,
  styleUrls: ['./app.component.css'],
})
export class AppComponent {
  title = 'default';
}
```
```angular-ts
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [],
  template: `
    <h1>Default</h1>
  `,
  styleUrl: './app.component.css',
})
export class AppComponent {
  title = 'default';
}
```
```angular-ts
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [],
  template: `
    <h1>Default</h1>
    {{1+1}}
  `,
  styleUrl: './app.component.css',
})
export class AppComponent {
  title = 'default';
}
```
````
---
layout: center
---

# Eventually you want to add some Logic?!

---
---

````md magic-move
```angular-ts
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [],
  template: `
    <div *ngIf="isAuthenticated">User is Authenticated</div>
    <div *ngIf="!isAuthenticated">User is not Authenticated</div>
  `,
  styleUrls: ['./app.component.css'],
})
export class AppComponent {
  isAuthenticated = true;
}
```
```angular-ts
import {Component} from '@angular/core';

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [],
  template: `
    @if(isAuthtenticated){
        <span>User is Authenticated</span>
    } @else {
        <span>User is not Authenticated</span>
    }
  `,
  styleUrls: ['./app.component.css'],
})
export class AppComponent {
  isAuthenticated = true;
}
```
````

---
layout: center
---

# Structural Directives vs Control Flow Syntax

---
---

# Structural Directives 10000 Feet View

<ul>
    <li>Logic that Affects the structure of a template</li>
    <li>Special kind of Directive</li>
    <li>Original Angular 2 and Higher</li>
</ul>

---
---

# Control Flow 10000 Feet View

<ul>
    <li>Logic that Affects the structure of a template</li>
    <li>Compiler-Magic</li>
    <li>Angular 17 and Higher</li>
    <li>Better API and Ergonomy</li>
</ul>

---
---

# Pros for Structural Directives

<ul>
    <li>Most Codebases are still using it!</li>
    <li>Can be customized</li>
    <li>You will automatically understand Control Flow</li>
</ul>

---
---

# # Pros for Control Flow

<ul>
    <li>More Intuitive</li>
    <li>Better Performance and Defaults</li>
    <li>Some Unique Features (@defer)</li>
</ul>


---
layout: center
---

# My Recommendation: Basics of Structural Directives and then move to Control Flow

---
---

# Ressources for Structural Directives

<ul>
    <li><a href="https://angular.dev/guide/directives#built-in-structural-directives" target="_blank">Angular Docs</a></li>
    <li><a href="https://dev.to/this-is-angular/mastering-angular-structural-directives-the-basics-jhk" target="_blank">4 Part Series by Robin Goetz</a></li>
    <li><a href="https://www.youtube.com/watch?v=07CaGlbMPbw" target="_blank">Video By Decoded Frontend</a></li>
</ul>

---
---

# Ressources for Control Flow

<ul>
    <li><a href="https://angular.dev/guide/templates/control-flow" target="_blank">Angular Docs</a></li>
    <li><a href="https://timdeschryver.dev/bits/angular-control-flow" target="_blank">Blog by Tim Deschryver</a></li>
    <li><a href="https://www.youtube.com/watch?v=hsUxJjY-PRg" target="_blank">Announcement Video By Angular Team</a></li>
    <li><a href="https://www.youtube.com/watch?v=77tKyAOFO4o" target="_blank">Video ByJoshua Morony</a></li>
</ul>

---
layout: image
image: /dark-souls-meme.png
backgroundSize: contain
---

---
layout: cover
---

# NgModules vs Standalone

---
---

<div class="flex w-full mb-8">
    <div class="w-full">
        <span class="text-4xl">NgModules</span>
    </div>
    <div class="w-full">
        <span class="text-4xl text-gray">Standalone</span>
    </div>
</div>
````md magic-move
```angular-ts
@NgModule({
    declarations: [AppComponent],
    imports: [BrowserModule, HttpClientModule],
    providers: [],
    bootstrap: [AppComponent]
})
export class AppModule {}
```
```angular-ts
@NgModule({
    declarations: [ChildComponent],
    imports: [CommonModule],
    providers: [],
    exports: [ChildComponent]
})
export class SubModule {}
```
```angular-ts
@NgModule({
    declarations: [ChildComponent],
    imports: [CommonModule],
    providers: [SomeFancyService],
    exports: [ChildComponent]
})
export class SubModule {}
```
````

---
---

<div class="flex w-full mb-8">
    <div class="w-full">
        <span class="text-4xl">NgModules</span>
    </div>
    <div class="w-full">
        <span class="text-4xl text-gray">Standalone</span>
    </div>
</div>
<ul>
    <li class="ml-0!" v-click>Confusing</li>
    <li class="ml-0!" v-click>Complex</li>
    <li class="ml-0!" v-click>Organizational-Purpose</li>
</ul>

---
---

<div class="flex w-full mb-8">
    <div class="w-full">
        <span class="text-4xl text-gray">NgModules</span>
    </div>
    <div class="w-full">
        <span class="text-4xl ">Standalone</span>
    </div>
</div>
````md magic-move
```angular-ts
@Component({
    selector: "app-parent",
    standalone: true,
    imports: [],
    providers: [],
    template: ``,
})
export class ParentComponent {}
```
```angular-ts
@Component({
    selector: "app-parent",
    standalone: true,
    imports: [ChildComponent],
    providers: [],
    template: `<app-child />`,
})
export class ParentComponent {}
```
```angular-ts
@Component({
    selector: "app-parent",
    standalone: true,
    imports: [ChildComponent],
    providers: [SomeFancyService],
    template: `<app-child />`,
})
export class ParentComponent {}
```
````

---
---

<div class="flex w-full mb-8">
    <div class="w-full">
        <span class="text-4xl text-gray">NgModules</span>
    </div>
    <div class="w-full">
        <span class="text-4xl ">Standalone</span>
    </div>
</div>
<ul>
    <li class="ml-0!" v-click>intuitive</li>
    <li class="ml-0!" v-click>similar to other frameworks</li>
    <li class="ml-0!" v-click>light-weight</li>
</ul>

---
---

<div class="flex w-full">
    <div class="w-full">
        <span class="text-4xl">NgModules</span>
        <ul class="mt-8">
            <li class="ml-0! mr-4!" v-click>heavily in-use</li>
            <li class="ml-0! mr-4!" v-click>won't go away any time soon</li>
        </ul>
    </div>
    <div class="w-full">
        <span class="text-4xl ">Standalone</span>
        <ul class="mt-8">
            <li class="ml-0!" v-click>easier to grasp</li>
            <li class="ml-0!" v-click>perfect for green-field</li>
        </ul>
    </div>
</div>

---
layout: center
---

# My Recommendation: Go with Modules
<span v-click>* This slide might need to be updated in 2025</span>

---
layout: center
---

# If you start from scratch: ditch Modules

<img src="https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExOWc0Nm5jZDB5aDd6MjIxMWJxd2FrcHI1c3JzcHpwa3doanc0cWtjeCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/1OZYnHCILinabxMF5H/giphy.webp" />

---
layout: cover
---

# Signals vs Observables

---
layout: cover
---

# Start with Signals

---
layout: cover
---

# But do Learn Observables

---
layout: cover
---

# Constructor Injection vs inject()

---
---

# Start with inject()

---
---

# Mostly a Personal Preference


---
layout: cover
---

# Signals Components vs Components

---
layout: cover
---

# Vite & esbuild vs Webpack


---
layout: cover
---

# SPA vs SSR

---
layout: outro
url: https://wordman.dev/talk/2024/kcjs
---
