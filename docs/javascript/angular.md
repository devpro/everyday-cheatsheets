# Angular

> One framework. Mobile & desktop.

→ [angular.io](https://angular.io/), [API](https://angular.io/api)

## History

Angular has replaced [AngularJS](https://angularjs.org/) (aka Angular v1).

## Releases

Version | Date | More
------- | ---- | ----
`13.0` | | [blog.ninja-squad.com](https://blog.ninja-squad.com/2021/11/03/what-is-new-angular-13.0/)
`12.0` | | [blog.ninja-squad.com](https://blog.ninja-squad.com/2021/05/12/what-is-new-angular-12.0/)
`10.0` | 2020-06-25 | [blog.angular.io](https://blog.angular.io/version-10-of-angular-now-available-78960babd41), [blog.ninja-squad.com](https://blog.ninja-squad.com/2020/06/25/what-is-new-angular-10.0/)

## Learn

### Training

- [Ninja Squad](https://ninja-squad.com/formations)

### Resources

- [Become a ninja with Angular - Pro Pack](https://angular-exercises.ninja-squad.com/)

### Books

- [Become a ninja with Angular - Ebook](https://books.ninja-squad.com/angular)

### Tutorials

- [github.com/devpro/dojo-angular-beginner](https://github.com/devpro/dojo-angular-beginner/blob/master/README.md)
- [web.dev](https://web.dev/angular)

### Libraries

- NgRx: [ngrx.io](https://ngrx.io/), [Documentation](https://ngrx.io/docs)

### Tools

- Visual Studio Code
  - [Using Angular in Visual Studio Code](https://code.visualstudio.com/docs/nodejs/angular-tutorial)

### Quick start

* Use [Angular CLI](./angular-cli.md)

```bash
# create the application
ng new

# launch locally (open http://localhost:4200)
ng serve --open

# add material theme
ng add @angular/material

# create the first module
ng generate module layout

# create the home page component
ng generate component layout/home
```

→ [angular.io/guide/quickstart](https://angular.io/guide/quickstart)

## Recipes

### Authentication

- [oktadeveloper/okta-angular-mongodb-hangman-example](https://github.com/oktadeveloper/okta-angular-mongodb-hangman-example)

### CI CD

#### Sonar

- Create a `sonar-project.properties` file at the root folder of the application

```ini
sonar.host.url=https://sonarcloud.io
sonar.login=<token>
sonar.organization=<company>
sonar.projectKey=<projetKey>
sonar.projectName=<projectName>
sonar.projectVersion=1.0
sonar.sourceEncoding=UTF-8
sonar.sources=src
sonar.exclusions=**/node_modules/**,**/*.spec.ts,**/coverage/**,**/bin/**,**/obj/**
#sonar.tests=test
sonar.test.inclusions=**/*.spec.ts
sonar.typescript.lcov.reportPaths=src/WebApp/ClientApp/coverage/lcov.info
#sonar.dotnet.visualstudio.solution.file=Solution.Name.sln
```

- Edit `package.json` file

{{< highlight json >}}
  "scripts": {
   "sonar": "node_modules/sonar-scanner/bin/sonar-scanner.bat"
  },
  "dependencies": {
    "sonar-scanner": "^3.1.0",
    "tslint-sonarts": "^1.8.0",
  }
{{< /highlight >}}

### Update

- Follow the procedure given at [update.angular.io](https://update.angular.io/)

### Web design

#### Material design

- [Material Design components for Angular](https://material.angular.io/)

#### DataTables

- Option 1: Angular Datatable
  - [Getting started](https://l-lin.github.io/angular-datatables/#/getting-started)

- Historique de la recherche :
  - [Angular 5 and jQuery DataTables !](https://medium.com/apprendre-le-web-avec-lior/angular-5-and-jquery-datatables-fd1dd2d81d99)
  - [10 Best Angular DataTables](https://www.ngdevelop.tech/best-angular-tables/)

#### materialize-css

- Home site: [materializecss.com](https://materializecss.com/getting-started.html)
- Integration in an Angular project:
  - Clean and ok: [How to use materialize-css with angular](https://stackoverflow.com/questions/48007665/how-to-use-materialize-css-with-angular)
  - Didn't work: [How to use MaterializeCSS in Angular 2](https://stackoverflow.com/questions/41937283/how-to-use-materializecss-in-angular-2)
  - Didn't also work: [stanleyeosakul/angular-travelville](https://github.com/stanleyeosakul/angular-travelville)
  - Didn't try: [sherweb/ngx-materialize](https://github.com/sherweb/ngx-materialize)
