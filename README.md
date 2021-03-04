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
            -> _config / utilities.scss (variables, funciones, loops, condicionales)
            -> _globales.scss
            -> _lib.scss (buttons, formularios, mixins y extends)
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

Las variables son elementos que podemos definir y asignarle un valor específico. En el caso de nuestro proyecto PlatziMusic tendrá algunas modificaciones. Para eso podemos usar las variables en los preprocesadores.

``` CSS
    $font-stack : Helvetica, sans-serif;
    $primary-color : #3333;

    body {
        font-size: $font-stack;
        color: $primary-color
    }
```

#### Reto

Como sabemos tenemos que hacer la guía de estilos del proyecto de PlatziMusic. En el reto te propongo que hagamos de forma predictiva las variables que serán utilizadas y los parciales que se pueden utilizar. Por ahora tenemos tablas, pero tendremos muchos más elementos útiles.

#### Solución al reto

Creamos los directorios y archivos necesarios para iniciar un proyecto cualquiera teniendo asi una plantilla pre definida.



