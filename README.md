# Angular_learning
This is for only my learning angular.

## memo
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
