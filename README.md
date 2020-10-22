# Angular_learning
This is for only my learning angular.

## memo
I did below things.
- `npm install -g @angular/cli`
- installed Angular language pack for visual studio.
- `ng new angular-app`
- pressed twice enter-key
- `ng serve` : run template project on local
- below 3 files are important for me.
    - `index.html`
    - `main.ts`
    - `style.css`
- main code of Angular is in `app` directory.
- some component are in `app`, and I can look some code like blow.
    - `app.component.html` : for view
    - `app.component.ts` : for performing
    - `app.component.css` : for styling
    - `app.component.spec.ts` : for testing
- `app.component.html` is only displaying some image and text. this html file is... not good for learning Angular.
- `app.component.ts` is constructed with 3 parts.
    - Loading module, it's for using `Component` from `@angular/core`.
    - `@Component` decorator. this is simple code.
        - selector : this is for writing component name in HTML. In this file, `app-root` is written here. So this component is used in `index.html` with `<app-root>`.
        - templateUrl : this is telling the file path for using as display html template file.
        - styleUrls : this is telling style sheet files.
        - well... `@Component` is telling some file of template html, style sheet and writing component as html tag.
    - Definition of `AppComponent` class
        - this is simple class what has only `title` property.
        - `export` before class name is for importing this component from other file. this is like below.
            ```
            class SampleClass {
                blahblahblah
            }

            export SampleClass;
            ```
- I don't need to look other `app.component` file because those file are not important for now.
 

