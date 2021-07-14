# Directivas

A grandes rasgos, una **directiva** nos permitira modificar la informacion que mostramos en nuestra plantilla

## Directiva NgIf

La directiva *NgIf* nos permite condicionar nuestro template, determinando si una condicion tiene resultado true or false

    <div *ngIf='mostrar'> Hola </div>  //hacemos alusion a que *mostrar* es un booleano

ngIf se utiliza como atributo de los selectores de tipo con un asterisco (*) de prefijo, y pasandole un booleando como valor

En este caso, el div al que le pasamos la directiva ngIf no se mostrará hasta que la variable mostrar no tenga el valor de true.

## Else en NgIf

Asi como en los lenguajes de programacion, dentro de Angular los condicionales NgIf tambien tienen un Else.

    <div *ngIf='mostrar; else nomostrar'> Hola </div>

    <ng-template #nomostrar>
        <p> Este es el resultado del else </p>
    </ng-template>

## Directiva NgFor

La sintaxis es similar a la de ngIf con pequeñas particularidades por su funcionalidad

    <div *ngFor = "let persona of personas ; let i = index"></div>

Lo que sucedera aqui es exactamente lo que sucede en un bucle for funcional. *Personas* equivale a un array, *persona* viene a ser
cada item del array personas (por lo que ngFor vendria a ser un .map/.forEach), y *let i="index"* equivale a el indice de cada elemento, el cual es autoincremental en 1. Entonces

    <div *ngFor = "let persona of personas ; let i = index">
        {{i}}    {{persona.nombre}} {{persona.apellido}}
    </div>

suponiendo que dentro del array personas encontramos un objeto con keys *nombre* y *apellido*, imprimimos primero su indice (el cual como ya se sabe, iniciara en 0), luego su nombre y finalmente su apelldo, y repetira esto con cada elemento del array





    



