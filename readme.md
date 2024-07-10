# INTRODUCCION A SASS

## CSS PLANO

Se refiere al uso de CSS sin ningún tipo de preprocesador.

```css
div {
  background-color: #242424;
}

div h1 {
  color: #fff;
  font-size: 40px;
}
```

## DESVENTAJAS DE CSS PLANO

- Puede resultar ser más dificil de mantener una estructura organizada cuando se trate de proyectos grandes.
- Sin la capacidad de crear módulos de estilos, cada archivo CSS puede volverse muy grande y dificil de manejar.
- Todo el CSS está en el mismo ámbito global, lo cual podría llevar a ocasionar conflictos de nombres y problemas de especificidad.
- Sin las capacidades de reutilización de código que ofrecen los preprocesadores, es común tener código repetitivo.

## QUE ES UN PREPROCESADOR

Es una herramienta que la cual permite al CSS tradicional el uso de variables, anidamiento, entre otras características. Se escribe el código en un lenguaje de preprocesador (Sass, LESS o Stylus) y luego éste lo compila en CSS estandar para que los navegadores puedan entenderlo.

## VENTAJAS DE UN PREPROCESADOR

- Permite definir y reutilizar valores como colores, fuentes y tamaños en todo nuestro proyecto.
- Permite escribir CSS de una manera que refleja la jerarquía del HTML, mejorando la legibilidad y organización de nuestro código.
- Facilita la división del CSS en archivos más pequeños y manejables

## QUE ES SASS

Es un procesador de CSS que extiende las capacidades del CSS tradicional al permitir el uso de variables, anidamientos y más, facilitando la escritura, organización y mantenimiento de nuestro codigo CSS.

## VARIABLES

Son entidades que almacenan valores reutilizables como colores, fuentes y tamaños, permitiendo una fácil gestión y actualización del estilo en nuestro proyecto.

```css
/* Definición de variables */
$primary-color: #007bff;
$secondary-color: #6c757d;
$font-stack: Helvetica, sans-serif;

body {
  font-family: $font-stack;
  color: $primary-color;
}

nav {
  background-color: $secondary-color;
}
```

## SCOPE

Define el contexto en el que las variables son accesibles. Las variables definidas dentro de un bloque solo están disponibles dentro de ese bloque, mientras que las variables globales están disponibles en todo el archivo.

```css
$global-color: #333; // Variable global

.container {
  $local-color: #007bff; /* Variable local */
  color: $local-color; /* Se puede usar dentro del mismo bloque */
}

.header {
  color: $global-color; /* Se puede usar en cualquier lugar */
}

/* color: $local-color; Esto causará un error porque $local-color no está en el scope global */
```

## ANIDAMIENTO

Permite escribir selectores CSS de manera jerárquica, reflejando la estructura del HTML y mejorando la legibilidad y organización del código.

```css
.nav {
  background-color: #333;
  ul {
    list-style: none;
    li {
      display: inline-block;
      a {
        text-decoration: none;
        color: white;
      }
    }
  }
}
```

## AMPERSAN PADRE

Se refiere al selecto padre en una regla anidada, permitiendo aplicar estilos contextuales y modificadores de manera más concisa.

```css
.button {
  color: white;
  background-color: blue;

  &:hover {
    background-color: darkblue;
  }

  &.active {
    background-color: green;
  }
}
```

## IMPORT

Se utiliza para importar archivos Sass dentro de otro archivo Sass, permitiendo modularizar y organizar el código de manera más efectiva.

\_variables.scss

```css
$primary-color: #007bff;
$secondary-color: #242424;
```

styles.scss

```css
@import 'variables';

body {
  font-family: Arial, sans-serif;
  color: $primary-color;
}

.header {
  background-color: $secondary-color;
  color: white;
  padding: 10px;
}
```
