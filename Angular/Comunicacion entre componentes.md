# Comunicacion entre componentes


## Property Binding entre componentes

Para recibir informacion en un componente hijo, desde un componete padre. Se utiliza el decorador *@Input()*
Con este lo que haremos sera recibir algun valor mediante property binding para posteriormente poder utilizarlo.

Seguido de input declararemos la variable en la que almacenaremos los datos del componente padre.

    .ts

    export class Persona {
        @Input() personaAlmacenada:string;
        @Input() indice:number;
        } 

    .html (padre)

    <app-persona
    *ngFor ="let persona of personas; let i = index"
    [personaAlmacenada]="persona"
    [indice]="i">
    </app-persona>

    .persona.html (hijo)

    <div>
    {{indice}} : {{personaAlmacenada.nombre}} {{personaAlmacenada.apellido}}
    </div>



Ts te pide inicializar la variable antes de utilizarla dentro del decorador @Input, por lo que podemos hacerlo, o directamente podemos esquivar esa restriccion declarando en el archivo ts.config

    "compilerOptions": {
    "strictPropertyInitialization": false,
    .....
    }


         


