# Angular_learning
This is for only my learning angular.

## Memo
### First step
- `npm install -g @angular/cli`
- Installed Angular language pack for visual studio.
- `ng new angular-app`
- Pressed twice enter-key
- `ng serve` : run template project on local
- Below 3 files are important for me.
    - `index.html`
    - `main.ts`
    - `style.css`
- Main code of Angular is in `app` directory.
- Some component are in `app`, and I can look some code like blow.
    - `app.component.html` : for view
    - `app.component.ts` : for performing
    - `app.component.css` : for styling
    - `app.component.spec.ts` : for testing
- `app.component.html` is only displaying some image and text. this html file is... not good for learning Angular.
- `app.component.ts` is constructed with 3 parts.
    - Loading module, it's for using `Component` from `@angular/core`.
    - `@Component` decorator. This is simple code.
        - selector : This is for writing component name in HTML. In this file, `app-root` is written here. So this component is used in `index.html` with `<app-root>`.
        - templateUrl : This is telling the file path for using as display html template file.
        - styleUrls : This is telling style sheet files.
        - Well... `@Component` is telling some file of template html, style sheet and writing component as html tag.
    - Definition of `AppComponent` class
        - This is simple class what has only `title` property.
        - `export` before class name is for importing this component from other file. this is like below.
            ```
            class SampleClass {
                blahblahblah
            }

            export SampleClass;
            ```
- I don't need to look other `app.component` file because those file are not important for now.
- `app.module.ts` is similar to `app.component.ts`. This is constructed with below 3 parts.
    - Importing part
        - `BrowserModule` : this is for running application on browser.
        - `NgModule` : this is for using `@NgModule` decorator.
    - `@NgModule` decorator part.
        - this is embedding angular module to parametered class.
        - this decorator has below.
            - declaration: For telling how many components are included.
            - imports: For telling other module what I use.
            - providers: For telling service provider. 
            - bootstrap: For specifing bootstrap.
    - Definition of AppModule class
        - this is for importing this component from other file.
        - this class is used in `main.ts`, and this class is also set as `bootstrapModule`. So, when I run this app, this `AppModule` is run first by `bootstrapModule`. next, `AppModule` run `AppComponent`.

### Creating component
The features are below.
- Constructing below.
    - HTML
    - Style sheet
    - Script
- Definition with `@Component` decorator.

I make `HelloComponent` as below step.
- Run `ng generate component hello`
- Check the update of `app.module.ts` as using `hello.component`. this component is written as `HelloComponent` in `app.module.ts`.
- Rewrite `app/hello/hello.component.html` as below
    ```
    <div id = "body">
        <h1>{{ title }}</h1>
        <p>{{ message }}</p>
    </div>
    ```
- Look `app/hello/hello.component.ts`
    - this file is importing `Component` and `OnInit`.
    - `OnInit` is interface for adding method call to initilize component.
- Update upper file as below.
    ```
    import { Component, OnInit } from '@angular/core';

    @Component({
        selector: 'app-hello',
        templateUrl: './hello.component.html',
        styleUrls: ['./hello.component.css']
    })
    export class HelloComponent implements OnInit {
        title:string
        message:string

        constructor() { }

        ngOnInit(): void {
            this.title = 'Hello-app'
            this.message = 'This is my first component'
        }
    }
    ```
    - `variable_name:type`
- Update `index.html` like below
    ```
    <body>
        <app-hello></app-hello>
    </body>
    ```
- Run `ng serve`
- Look nothing on browser at `http://localhost:4200`.
- Update `app.module.ts` as below.
    ```
    bootstrap: [HelloComponent]
    ```
- Run `ng serve` again or look browser. Then I can the page like this.

    ![image](https://user-images.githubusercontent.com/5573785/96905612-a2fbd480-14d3-11eb-938b-cf7e9cb19340.png)

Changing style sheet
- update `app/hello/hello.component.css` as below
    ```
    #body {
        margin-top: 75px;
    }

    h1 {
        font-size: 60pt;
        letter-spacing: -5px;
        color: lightblue;
        position: absolute;
        top: -70px;
        right: 0px;
    }

    p {
        font-size: 18pt;
    }
    ```
- Run `ng serve` or look browser. Then I can the page like this.

    ![image](https://user-images.githubusercontent.com/5573785/96906455-c70be580-14d4-11eb-8ef9-43d3dab5efb1.png)

`{{ }}` can be used for calc.
- Write `<p>Result: {{ 12300 * 1.08 }} yen</p>` in `app/hello/hello.component.html`
    ```
    <div id = "body">
        <h1>{{ title }}</h1>
        <p>{{ message }}</p>
        <p>Result: {{ 12300 * 1.08 }} yen</p>
    </div>
    ```
- Run `ng serve` or look browser. Then I can the page like this.

    ![image](https://user-images.githubusercontent.com/5573785/96906766-426d9700-14d5-11eb-8860-e701d77b0077.png)

Calc with property
- Update `app/hello/hello.component.html` as below
    ```
    <div id = "body">
        <h1>{{ title }}</h1>
        <p>{{ message }}</p>
        <p>Result: {{ price * 1.08 }} yen</p>
    </div>
    ```
- Update `app/hello/hello.component.ts` as below
    ```
    import { Component, OnInit } from '@angular/core';

    @Component({
        selector: 'app-hello',
        templateUrl: './hello.component.html',
        styleUrls: ['./hello.component.css']
    })
    export class HelloComponent implements OnInit {
        title:string
        message:string
        price:number

        constructor() { }

        ngOnInit(): void {
            this.title = 'Hello-app'
            this.message = 'This is my first component'
            this.price = 123450
        }
    }
    ```
- Run `ng serve` or look browser. Then I can look the page like below.

    ![image](https://user-images.githubusercontent.com/5573785/96907190-da6b8080-14d5-11eb-8754-460a1ef5395d.png)

Method calling with `{{ }}`
- `{{ }}` is not only displaying variable. I can everything what I prepared before.
- For displaying Time, I make function `today` in `app/hello/hello.component.ts`
    ```
    today() {
        return new Date().toLocaleString()
    }
    ```
- Update `app/hello/hello.component.html` as below.
    ```
    <div id = "body">
        <h1>{{ title }}</h1>
        <p>{{ message }}</p>
        <p>Result: {{ price * 1.08 }} yen</p>
        <p>Today: {{ today() }}</p>
    </div>
    ```
- Run `ng serve` or look browser. Then I can look the page like below.

    ![image](https://user-images.githubusercontent.com/5573785/96907844-c1af9a80-14d6-11eb-88d2-dc3dd42b6941.png)

Updating property
- The value of `{{ }}` is not only displaying the value. The value is available after displaying the page, and it's always updated.
- Update `app/hello/hello.component.ts` as below
    ```
    import { Component, OnInit } from '@angular/core';
    import { Data } from '@angular/router';

    @Component({
        selector: 'app-hello',
        templateUrl: './hello.component.html',
        styleUrls: ['./hello.component.css']
    })
    export class HelloComponent implements OnInit {
        title:string
        message:string
        price:number
        now:Date

        constructor() {
            setInterval(() => this.now = new Date(), 1000)
        }

        ngOnInit(): void {
            this.title = 'Hello-app'
            this.message = 'This is my first component'
            this.price = 123450
        }

        today() {
            return this.now.toLocaleString()
        }
    }
    ```
- Run `ng serve` or look browser. Then I can look the page like below.

    ![sample](https://user-images.githubusercontent.com/5573785/96909013-5ff03000-14d8-11eb-8f0a-715d41303f46.gif)

Setting value to element
- I learned setting value to `<p> blahblah </p>` with `{{ }}`. But I can set value to element.
- Element is ... `<div element=blahblahblah>`. Well I can set it as `<div [element]="property name">`. I can't use `{{ }}` into the part of property name.
- Update `app/hello/hello.component.html` as below.
    ```
    <div id = "body">
        <h1>{{ title }}</h1>
        <p>{{ message }}</p>
        <p [class]="styleClass" >{{ message }}</p>
        <p>Result: {{ price * 1.08 }} yen</p>
        <p>Today: {{ today() }}</p>
    </div>
    ```
- Update `app/hello/hello.component.ts` as below
    ```
    import { Component, OnInit } from '@angular/core';
    import { Data } from '@angular/router';

    @Component({
        selector: 'app-hello',
        templateUrl: './hello.component.html',
        styleUrls: ['./hello.component.css']
    })
    export class HelloComponent implements OnInit {
        title:string
        message:string
        price:number
        now:Date
        styleClass:string

        constructor() {
            setInterval(() => this.now = new Date(), 1000)
        }

        ngOnInit(): void {
            this.title = 'Hello-app'
            this.message = 'This is my first component'
            this.price = 123450
            this.styleClass = 'red'
        }

        today() {
            return this.now.toLocaleString()
        }
    }
    ```
- Add below into `app/hello/hello.component.css` 
    ```
    .red {
        color: white;
        background-color: red;
    }
    ```
- Run `ng serve` again or look browser. Then I can look the page as below.

    ![image](https://user-images.githubusercontent.com/5573785/96975854-0c242c00-1556-11eb-8dfa-4aab58c4c011.png)
