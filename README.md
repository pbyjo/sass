# Curso de Sass 🎨

### M2 - Instalación

#### Estructura css

 >Clase 5

La primera ventaja que se nos ocurre es que podemos organizar nuestro Sass. Lo clave es que podemos separar nuestro código en archivos (volver nuestro proyecto modular). Ya no tenemos que revisar un archivo muy amplio, sino que podemos hacer modificaciones a un solo archivo, lo que nos hace el trabajo mucho más fácil.

`_name.scss` guión abajo nos permite decirle a sass que este archivo modular no compila, ya que no es el archivo main que recibe todos los archivos modulares.

```
proyect
    -> public
        -> .html
        -> .css
    -> styles
        -> lib
            -> _config.scss (variables, fuentes, config inicial)
            -> _utilities.scss (mixins & include, extends, condiciones, funciones, loops, content)
            -> _globales.scss
            -> _lib.scss (buttons, formularios)
            -> _components.scss
            -> _features.scss
            -> _header.scss
            -> _footer.scss
            -> _modals.scss
            -> _animations.scss
        -> .scss
    -> items
        -> logos
        -> images
        -> videos
        -> fonts
        -> icons
    -> javascript
```

### M3 - Variables

#### variables

 >Clase 6

Las variables son elementos que podemos definir y asignarle un valor específico. En el caso de nuestro proyecto PlatziMusic tendrá algunas modificaciones. Para eso podemos usar las variables en los preprocesadores.

``` CSS
    $font-stack : Helvetica, sans-serif;
    $primary-color : #3333;

    body {
        font-size: $font-stack;
        color: $primary-color
    }
```

Para escapar una variable se usa el comodín #.

Esto es necesario en casos como, por ejemplo, cuando la variable está rodeada por comillas y de no ponerse el escape la variable pasaría como una cadena de caracteres..

``` scss
$size: 10;

div {
  content: "#{$size}"
}
```

#### Reto

 >Clase 7

Como sabemos tenemos que hacer la guía de estilos del proyecto de PlatziMusic. En el reto te propongo que hagamos de forma predictiva las variables que serán utilizadas y los parciales que se pueden utilizar. Por ahora tenemos tablas, pero tendremos muchos más elementos útiles.

#### Solución al reto

 >Clase 8

Creamos los directorios y archivos necesarios para iniciar un proyecto cualquiera teniendo asi una plantilla pre definida.

#### Anidaciones

 >Clase 9

Ejemplo: 

``` scss
.Block {

	&__Element {

		&--Modifier {

		}
	}
}

.btn {
        display: inline-block;
        font-size: $button-fontsize;
        border-radius: $border-radius;
        color: $button-color;
        background-color: $button-bgcolor;
        @extend .line-height;

        &__icon {
                font-size: .6em;
        }

        &--info {
                background-color: $info-color;
        }
}

.btn {
  color: red;
  &:hover {
    color:blue;
  }
}
```

### M5 - Mixins

#### Mixins

 >Clase 10

Los mixins nos ayudan a reciclar declaraciones para evitar mucho trabajo. Para esto vamos a usar `@mixin`

Cuando se define un mixin, los argumentos se definen como una serie de variables separadas por comas, y todo ello encerrado entre paréntesis.

``` scss
    @mixin max-width($max-width: 0px) {
        max-width: $max-width
        margin-left: auto
        margin-right: auto
    }
```

En este caso le estamos definiendo un valor por defecto. Si deseamos cambiar ese valor, cuando lo llamemos se lo podemos cambiar de esta forma:

``` scss
    @include max-width(1200px)
```

#### Mixins pt II

 >Clase 11

Para crear encabezados responsivos según el ancho de pantalla.

``` scss 
@mixin encabezado($font-size) {
    @for $i from 1 through 3 {
        h#{$i} {
            @if $i == 1 {
                font-size: $font-size - $i * 0;
            }
            @else {
                font-size: $font-size - $i * .15;
            }
        }
    }
}

@include encabezado(1.5em);

@media (min-width: 800px){
    @include encabezado(2em);
}
@media (min-width: 1200px){
    @include encabezado(2.5em);
}
```

Los **mixins** nos permite recibir parámetros, esta funcionalidad nos ayuda bastante, ya que con un solo mixins podemos obtener distintas salidas con solo cambiar el valor del parámetro.

#### Uso de la directiva 'content' (block en stylus)

 >Clase 12

Una de las características que tienen los mixins es la directiva content. Esta nos permite incluir un bloque de contenido dentro de un mixin.

``` scss 
@mixin response-to($width) {
  @media only screen and (min-width: $width) {
    @content;
  }
}

section {
  background: blue;
  @include response-to(800px) {
    background-color: red;
  };
}
```

**Media queries template**

``` scss

@mixin media ($breakpoint) {  

  @if $breakpoint == tablet {  
    @media only screen and (min-width: 768px) { @content; }  
  }  
  
  @else if $breakpoint == desktop-s {  
    @media only screen and (min-width: 992px) { @content; }  
  } 
  
  @else if $breakpoint == desktop-m {  
    @media only screen and (min-width: 1200px) { @content; }  
  } 
  
  @else if $breakpoint == desktop-l {  
    @media only screen and (min-width: 1480px) { @content; }  
  } 
  
  @else if $breakpoint == desktop-xl {  
    @media only screen and (min-width: 1780px) { @content; }  
  } 

  @else if $breakpoint == mobile-only {  
    @media only screen and (max-width: 768px) { @content; }  
  }

  @else if $breakpoint == tablet-p-only {  
    @media only screen and (min-width: 768px) and (max-width: 992px) and (orientation : portrait) { @content; }  
  }  
  
  @else if $breakpoint == tablet-l-only {  
    @media only screen and (min-width: 768px) and (max-width: 992px) and (orientation : landscape) { @content; }  
  } 
  
  @else if $breakpoint == desktop-s-only {  
    @media only screen and (min-width: 768px) and (max-width: 1200px) { @content; }  
  } 
  
  @else if $breakpoint == desktop-m-only {  
    @media only screen and (min-width: 1200px) and (max-width: 1480px) { @content; }  
  } 
} 
```

#### Extend 

 >Clase 13



