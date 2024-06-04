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
    <img  src="/first-commit.png" style="width:65%"/>
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

<style>
    li {
        padding-top: 1rem;
        padding-bottom: 1rem;
    }
</style>

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

# Resources for Structural Directives

<ul>
    <li><a href="https://angular.dev/guide/directives#built-in-structural-directives" target="_blank">Angular Docs</a></li>
    <li><a href="https://dev.to/this-is-angular/mastering-angular-structural-directives-the-basics-jhk" target="_blank">4 Part Series by Robin Goetz</a></li>
    <li><a href="https://www.youtube.com/watch?v=07CaGlbMPbw" target="_blank">Video By Decoded Frontend</a></li>
</ul>

---
---

# Resources for Control Flow

<ul>
    <li><a href="https://angular.dev/guide/templates/control-flow" target="_blank">Angular Docs</a></li>
    <li><a href="https://timdeschryver.dev/bits/angular-control-flow" target="_blank">Blog by Tim Deschryver</a></li>
    <li><a href="https://www.youtube.com/watch?v=hsUxJjY-PRg" target="_blank">Announcement Video By Angular Team</a></li>
    <li><a href="https://www.youtube.com/watch?v=77tKyAOFO4o" target="_blank">Video ByJoshua Morony</a></li>
</ul>

<style>
    li {
        padding-top: 1rem;
        padding-bottom: 1rem;
    }
</style>

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
---
# Resources for NgModules

<ul>
    <li><a href="https://angular.dev/guide/ngmodules" target="_blank">Angular Docs</a></li>
    <li><a href="https://blog.angular-university.io/angular2-ngmodule/" target="_blank">Angular University</a></li>
    <li><a href="https://www.youtube.com/watch?v=oqZ4-ULwfbc" target="_blank">Video By Fireship</a></li>
</ul>

---
---

# Resources for Standalone Components

<ul>
    <li><a href="https://www.angulararchitects.io/en/blog/angulars-future-without-ngmodules-lightweight-solutions-on-top-of-standalone-components/" target="_blank">8 Part Series by Manfred Steyer</a></li>
    <li><a href="https://blog.angular-university.io/angular-standalone-components/" target="_blank">4 Part Series by Robin Goetz</a></li>
    <li><a href="https://www.youtube.com/watch?v=c8YGsPx0zVk" target="_blank">Video By Deborah Kurata</a></li>
</ul>

---
layout: cover
transition: view-transition
---

<div class="w-full flex justify-between">
    <h1 class="inline-block" style="view-transition-name: signals-headline"> Signals</h1> <h1 class="inline-block">vs</h1> <h1 class="inline-block"  style="view-transition-name: observable-headline">Observables</h1>
</div>

---
layout: cover
---

<div class="flex w-full mb-8">
    <div class="w-full">
        <span class="text-4xl" style="view-transition-name: signals-headline">Signals</span>
    </div>
    <div class="w-full">
        <span class="text-4xl" style="view-transition-name: observable-headline">Observables</span>
    </div>
</div>
<div class="flex w-full mb-8" v-click>
    <ul class="w-full">
        <li class="ml-0! mr-4!">Stateful</li>
        <li class="ml-0! mr-4!">1 Value</li>
        <li class="ml-0! mr-4!">Synchronous</li>
    </ul>
    <ul class="w-full">
        <li class="ml-0!">Stateless</li>
        <li class="ml-0!">0 to Infinite Values</li>
        <li class="ml-0!">Synchronous or <span v-mark.circle.red="2">Asynchronous</span></li>
    </ul>   
</div>

---
layout: cover
---

<div class="flex w-full mb-8">
    <div class="w-full">
        <span class="text-4xl" style="view-transition-name: signals-headline">Signals</span>
    </div>
    <div class="w-full">
        <span class="text-4xl" style="view-transition-name: observable-headline">Observables</span>
    </div>
</div>
<div class="flex w-full mb-8">
    <ul class="w-full">
        <li class="ml-0! mr-4!">Everything that is rendered</li>
        <li class="ml-0! mr-4!">performant rendering</li>
    </ul>
    <ul class="w-full">
        <li class="ml-0!">Event Coordination</li>
        <li class="ml-0!">Cancellation</li>
        <li class="ml-0!"><span v-mark.red>Asynchronous</span></li>
    </ul>   
</div>

---
layout: cover
---
## My Recommendation
# Start with Signals

---
layout: cover
---

## My Recommendation
# But do Learn Observables
---
---
# Resources for Signals

<ul>
    <li><a href="https://angular.dev/guide/signals" target="_blank">Angular Docs</a></li>
    <li><a href="https://angular-signals.dev/" target="_blank">Signals Course by Maciej Wojcik</a></li>
    <li><a href="https://www.youtube.com/watch?v=Qy-oUc5eB2M" target="_blank">Video By the Angular Team</a></li>
</ul>

---
---

# Resources for Observables

<ul>
    <li><a href="https://rxjs.dev/guide/observable" target="_blank">RxJS Docs</a></li>
    <li><a href="https://codecraft.tv/courses/angular/reactive-programming-with-rxjs/observables-and-rxjs/" target="_blank">Blog by Asim Hussain</a></li>
    <li><a href="https://www.youtube.com/watch?v=m40cF91F8_A" target="_blank">Talk By Ben Lesh</a></li>
</ul>

---
layout: cover
---

# Constructor Injection vs Inject()

---
layout: cover
---

````md magic-move

```angular-ts
@Component({})
class SomeComponent {
    constructor(){}
}
```
```angular-ts
@Component({})
class SomeComponent {
    constructor(private httpClient: HttpClient){}
}
```
```angular-ts
@Component({})
class SomeComponent {
    private httpClient = inject(HttpClient);
}
```
````
---
layout: cover
---

# Constructor Injection is pretty intuitive
## Inject Function has some pitfalls

---
---
````md magic-move
```angular-ts
const load = () => {
  const foo = inject(FooService);
  foo.doSome();
};

@Component({
  selector: 'my-app',
  template: `in app! <button (click)="onClick()">click </button>`,
})
export class AppComponent {
  name = 'Angular ' + VERSION.major;

  onClick() {
    load();
  }
}
```
```shell
Error: NG0203: inject() must be called from an injection context 
(a constructor, a factory function or a field initializer)

```
```angular-ts{*|12|15-17}
const load = () => {
  const foo = inject(FooService);
  foo.doSome();
};

@Component({
  selector: 'my-app',
  template: `in app! <button (click)="onClick()">click </button>`,
})
export class AppComponent {
  name = 'Angular ' + VERSION.major;
  private injector = inject(EnvironmentInjector)

  onClick() {
    this.injector.runInContext(() => {
      load(); // in this context, injections are allowed. 
    });
  }
}
```
````

---
---
````md magic-move
```angular-ts
const getCharacters = () => {
    const httpClient = inject(HttpClient);
    const destroyRef = inject(DestroyRef);
    return httpClient.get("https://rickandmortyapi.com/api/character").pipe(
        catchError((e) => {
            console.error({e})
            return of([]);
        }),
        takeUntilDestroyed(this.destroyRef)
    )
}
```
```angular-ts
@Component({})
public RickAndMortyCharacterListComponent {
    protected characters = inject(getCharacters())
}
```
```angular-ts {*|1|6-7|9|11-22|19|26}
export const resourceService = <T>(
  endpoint: string,
  initialValue: T,
  providedIn?: 'root'
) => {
  @Injectable({ providedIn: providedIn ?? null })
  class SomeService {
    private http = inject(HttpClient);
    public data = signal<T>(initialValue);
    public pending = signal(false);

    constructor() {
      defer(() => {
        this.pending.set(true);
        return this.http.get<T>(endpoint);
      })
        .pipe(
          finalize(() => this.pending.set(false)),
          takeUntilDestroyed()
        )
        .subscribe((result) => {
          this.data.set(result);
        });
    }
  }
  return SomeService;
};
```

```angular-ts
export const RickAndMortyService = resourceService<any>(
  'https://rickandmortyapi.com/api/character',
  []
);
```
```angular-ts
@Component({
providers: [RickAndMortyService]
})
class Component{
    private rickAndMortyService = inject(RickAndMortyService)
}
```
````


---
layout: cover
---

# Start with inject()
## Mostly a personal preference though
---
---

# Resources for Constructor Injection

<ul>
    <li><a href="https://angular.dev/guide/di" target="_blank">Angular Docs</a></li>
    <li><a href="https://blog.angular-university.io/angular-dependency-injection/" target="_blank">Blog by Angular University</a></li>
    <li><a href="https://www.youtube.com/watch?v=G8zXugcYd7o&list=PLX7eV3JL9sfmJ6AaZj9eDlAKrJrEul4Vz" target="_blank">Videos By the Decoded Frontend</a></li>
</ul>

---
---

# Resources for inject() function

<ul>
    <li><a href="https://angular.dev/guide/di" target="_blank">Angular Docs</a></li>
    <li><a href="https://marmicode.io/blog/angular-inject-and-injection-functions/" target="_blank">Blog by Younes Jaaidi</a></li>
    <li><a href="https://nartc.me/blog/inject-function-the-right-way/" target="_blank">Blog by Chau Tran</a></li>
    <li><a href="https://www.youtube.com/watch?v=_quyWq4NnRM" target="_blank">Videos By the Joshua Morony</a></li>
</ul>

<style>
    li {
        padding-top: 1rem;
        padding-bottom: 1rem;
    }
</style>

---
layout: outro
url: https://wordman.dev/talk/2024/frontend-nation
---
