
# Angular
## [Universidad Angular 2021](https://www.udemy.com/course/angular-de-cero-a-experto-angular-2-framework-javascript-html-css)


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

## Creacion de un componente con CLI

Dentro del CLI de Angular, existe un comando que simplifica el inicio de la creacion de nuestros componentes. Para crear un "boilerplate" generico de un componente podemos utilizar en consola

    ng generate componente *nombre-del-componente*
    ng g c *nombre-del-componente*

Esto nos creará una carpeta de componente con el nombre que le hayamos pasado, donde adentro seteará cuatro archivos ( HTML - CSS - TS - SPEC ) para iniciar nuestro codeo mas rapido.

## Creación de un componente Inline

La modularización es una gran práctica, ya que ordena nuestros proyectos dejando el codigo mucho mas limpio y estructurado. Sin embargo no tiene mucho sentido modularizar por 3 lineas de código.

Por este motivo en los decoradores *@Component* de Angular existe, aparte del atributo *TemplateUrl* un atributo extra llamado ***template*** en el cual podemos escribir el codigo HTML dentro del *component* archivo, de forma INLINE

    @Component({
        selector:'app-persona',
        template:'<div><h1>Hola<h1></div>'
    })

Para poder utilizar saltos de linea, podriamos escribir lo mismo con backtiks (`)

    @Component({
        selector:'app-persona',
        template:`<div>
        <h1> Hola <h1>
        </div>`,
    })

Tambien existe un comando de Angular CLI para generar automaticamente componentes INLINE

## Configurando Bootstrap en Angular

Para realizar la instalacion, ejecutamos el comando de Bootstrap que nos muestra en la documentación ofiial

    npm install bootstrap --save
    npm install jquery --save 
    npm install popper.js --save

*(Actualmente en 2021 se debe instalar aun jquery y popper para evitar posibles errores de Bootstrap ya que la librería aún los utiliza. Es probable que omitir esas instalaciones no cause problemas pero ante la duda no esta de mas instalarlos)*

Luego debemos buscar la configuracion de los estilos en el archivo *angular.json*, alli se encontrara un atributo *styles* el cual contiene un array. Agregando una coma (,) a continuacion del archivo de estilos seteado por defecto, agregaremos la configuracion donde se encuentra nuestro archivo de Bootstrap

    ...
    "styles":[
        "src/styles.css",
        "node_modules/bootstrap/dist/css/bootstrap.min.css"
    ],
    ...

Y finalmente debemos agregar los scripts que utilizara bootstrap

    ...
    "scripts": [
            "node_modules/jquery/dist/jquery.slim.min.js",
            "node_modules/popper.js/dist/umd/popper.min.js",
            "node_modules/bootstrap/dist/js/bootstrap.min.js"
        ],
    ...

## Estilos en Angular

Como ya se vio previamente, para poder dar estilos en Angular es necesario indicar la ruta del archivo css (o preprocesador configurado) donde se encontraran los estilos que se deben utilizar en nuestro componente. Esto se configura en el decorador *@Component* dentro de la carpeta *.component.ts*

    ...@Component({
        ...
        styleUrl:['./app.component.css']
        style:`
            h1{
                color:green;
            }
            `
    })

Asi como con los template, tambien existe un atributo para setear estilos en linea

# Elementos Básicos

## Interpolación de datos

La interpolacion se trata de agregar texto dinamico en las plantillas HTML.

Para manejar la interpolacion se utiliza la sintaxis de doble llave ( {{}} ) con el nombre de nuestra variable dentro, variable que debe estar declarada en nuestra clase dentro del component.ts

    ...
    export class Persona{
        nombre:string="Juan"
    }

    ...
    /
    ...
    <div> {{nombre}} </div>

Asi como una variable, con el resultado de la interpolacion se pueden realizar distintas acciones (operaciones matematicas, metodos, etc)

## Template Reference Variable

Asi como la interpolación accede al valor de las variables dentro de la clase de nuestro componente, tambien puede acceder al valor de nuestros atributos HTML dentro del template 

    <div (keyup)="0">
        <input #entrada />
        {{entrada.value}}
    </div>

Con esta sintaxis, lo que logramos es acceder al valor de nuestros atributos HTML asignandole una variable a los valores que nos devuelve, mediente el atributo *#entrada*

## Property Binding

Este concepto se basa en la posibilidad de asignarle un valor a las propiedades de nuestros elementos HTML.

Con esto lo que podremos sera manipular de forma dinamica el valor de los atributos de nuestros elementos HTML con algo similar a la interpolacion

    ...html

    <button class="boton" [disabled]="deshabilitar"> </button>


    ...ts

    export class Boton{
        deshabilitar:boolean= true
    }

Como vemos aqui, declaramos en el component.ts una variable con la cual manipularemos el estado del boton. En este momento el boton se encuentra activo debido al valor *true* de nuestra variable *deshabilitar*

## Event Binding

En Angular, los eventos de un tag HTML se llaman con una sintaxis levemente distinta.
En lugar de introducir la palabra On como prefijo del evento, se llama entre parentesis

    (click)
    (change)
    (submit)

Asi como ejecutamos el Property Binding, de igual manera se puede utilizar con eventos:


    ...HTML
    <button 
        class="btn btn-primary" 
        [disabled]="deshabilitar"
        (click)='agregarPersona()'>

        Agregar Persona

    </button>

    ...Ts

    export class PersonasComponent{
    deshabilitar:boolean=false
    mensaje:string='No se ha agregado nada'

    agregarPersona=():void=>{
            if(this.mensaje==="No se ha agregado nada"){
                this.mensaje="Persona agregada";
                this.deshabilitar=true
            };
        }
    }

(En este ejemplo, estamos cambiando el valor de la variable dentro del tag *p* en base a la interpolacion del string *mensaje*, y tambien el atributo disabled del *button*
Al hacer click, el mensaje cambiara y tambien se deshabilitara nuestro botón gracias al Event y Property Binding)

En cuanto a los input, podemos tambien trabajar en tiempo real con la informacion que va siendo proporcionada dentro de ellos.

    ...HTML

    <input type="text" (input)="modificarTitulo($event)"> 

    ...TS


    export class Input{
        titulo=""

        modificarTitulo(event:Event){
            this.titulo= (<HTMLInputElement>event.target).value;
        }
    }

Aqui lo que sucede es que declaramos un metodo llamado modificarTitulo() el cual toma una variable, y setea la variable Titulo con su valor. 
Con esta funcion, dentro del HTML, logramos que el input mediante el evento (input) nos entregue su valor para poder pasarlo como argumento de modificarTitulo

## Two way binding

Esta es una forma de intercomunicar nuestros componentes, es decir que asi como anteriormente enlazamos nuestro HTML hacia el componente, tambien enlazaremos nuestro componente hacia el HTML.


Para esto necesitaremos importar un modulo nuevo a nuestro app.module

    ...module

    @NgModule({
        imports:[
            BrowserModule,
            FormsModule
        ]
    })














    


















