
# Angular
## Universidad Angular 2021 

https://www.udemy.com/course/angular-de-cero-a-experto-angular-2-framework-javascript-html-css
# Introducción

Angular es es un **framework** de JavaScript para construir y desarrollar aplicaciones tanto web como mobile.

Es un framework rapido y con un perfomance adecuado para realizar aplicaciones con una escalabilidad alta, basado en paginas de tipo SPA (Single Page Application: basada en un unico HTML).

Angular basa su construcción en el lenguaje TypeScript

## Requerimientos

- Conocimientos en JavaScript, HTML y CSS
- Conocimientos en Typescript
- Node Js
- NPM
- Editor de codigo

## Instalación
- Angular CLI :

    Para utilizar angular lo primero que debemos instalar es su CLI (Command Line Interface/ Consola)

    Para ello ejecutaremos el comando

        npm install -g @angular/cli (Windows)
        sudo npm install -g @angular/cli (Mac/Linux)

- Boilerplate automático:

    Asi como en React con create-react-app, este framework de JavaScript tiene un comando independiente para la instalacion de un boilerplate
    basico, el cual es

        ng new *nombre-de-la-app*

    Al dar enter, nos preguntara si queremos instalar el modo estricto (a lo que en general no afecta nada aceptar), Angular Routing (en general es util, pero en caso de estar aprendiendo los conceptios iniciales, se puede denegar para ocupar menos cantidad de memoria) y que tipo de hojas de estilo utilizaremos (CSS, Less, Sass, etc).

## Iniciar / Detener servidor

Para ejecutar la aplicacion en un servidor local debemos ingresar al boilerplate de nuestro proyecto mediante el comando...

    cd *nombre-de-la-carpeta*

...e introducir el siguiente comando

    ng serve

    ng serve -o (para abrir en el navegador la vista previa automaticamente)

Para detenerlo debemos ejecutar

    Tecla CTRL + C  ---->   Y

# Fundamentos

## Flujo de una aplicacion Angular

- Main ts

    Es el archivo donde se configura el levantamiendo del proyecto (index en React).
    Aqui podemos encontrar el AppModule que es el modulo raiz por defecto, con otras funciones propias del ng new de Angular

        import { enableProdMode } from '@angular/core';
        import { platformBrowserDinamic } from '@angular/platform-browser';

        import { AppModule } from './app/app.module';
        import { enviroment } from './enviroments/enviroment.ts';

        if (enviroment.production) {
            enableProdMode();
        }

        platformBrowserDynamic().bootstrapModule(AppModule)
        .catch(err => console.error(err));

- app.module.ts

    Es el modulo principal por defecto de Angular, donde se encuentra la configuracion y el decorador NgModule, el cual contiene 

        declarations: declaraciones del componente raiz
        imports: ni idea
        providers: asumo que es para el redux de angular
        bootstrap: es el atributo que setea el levantamiento de la aplicacion

            import {BrowserModule} from '@angular/platform-browser'
            import {NgModule} from '@angular/core'
            import {AppComponent} from './app.component'

            @NgModule({
                declarations:[
                    AppComponent
                    ],
                imports:[
                    BrowserModule
                    ],
                providers:[],
                bootstrap:[
                    AppComponent
                    ]
            })

            export class AppModule { }

- app.component.ts

    Este archivo dentro lleva la configuracion inicial del componente, dentro de lo que se encuentra

        El decorador @Component 

        La clase del componente qe contiene las variables:

        • selector = contiene el nombre del componente
        • templateUrl= contiene la ruta al html 
        • styleUrls= un array con las rutas de los css

            import {Component} from '@angular/core'

            @Component({
                selector: 'app-root',
                templateUrl: './app.component.html'
                styleUrls: ['./app.component.css']
            })

            export class AppComponent {
                title: 'Mi Primer App'
            }
    
- app.component.html

    Es el template del html de cada componente.

    En react seria el equivalente al JSX introducido dentro del return/render de un componente

    No requiere un import ya que esta conectado mediante el app.component

        <span>{{title}}</span>

## Creacion Manual de un Componente

En Angular los componentes se nombran

    *nombre-componente*.component.ts

El hecho de escribir *.component* no es una sintaxis obligatoria aunque se considera un convencion y gran practica incluirlo.

A diferencia de React, los componentes se nombran con minuscula como cualquier otro archivo.

- Lo primero que se debe definir es **la clase** de nuestro componente

    export class PersonasComponent{
    }

- No debemos olvidarnos del decorador **@Component** (debemos importarla de @angular/core)

    import {Component} from '@angular/core'

    @Component({

    })

- Luego de importar y declarar el decorador @Component, introduciremos los atributos correpondientes a nuerstro componente

    @Component({
        selector:'app-personas',
        templateUrl:'./personas.component.html'
    })

- Registrar un componente

    En el app.module debemos registrar el componente (Algo asi como las rutas de react)
     
    Para ello, dentro  de la clave *declarations* debemos declarar un nuevo indice denntro del array con la importacion de la clase del componente.

        ...
        import { PersonasComponent } from './personas/personas.component'

        @NgModule({
            declarations:[
                AppComponent, PersonasComponent
            ]
        })

- Renderizar nuestro nuevo componente

    Para poder utilizarlo, simplemente nos falta declararlo dentro de nustro html














