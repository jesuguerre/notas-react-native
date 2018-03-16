# Nuestro primer componente React Native

- - -
Esta guía asume que has [configurado TypeScript][1] en tu proyecto. Puedes
seguir la guía saltándote las partes específicas de TypeScript.
- - -

La forma más sencilla de empezar con React será crear un componente muy básico,
pero con el que aprenderemos los valores más importantes.

```typescript
// App.tsx

import * as React from 'react';
import { Text } from 'react-native';

interface PropsTexto {
    contenido: string;
}

const MiTexto = (props: PropsTexto) => {
    return <Text>{props.contenido}</Texto>;
}

export default MiTexto;
```

Ahora vamos a ver cada parte por separado. Las dos primeras líneas simplemente
importan la librería `React` y el componente básico [`Text`][2] para que podamos
usarlos.

```typescript
interface PropsTexto {
    contenido: string;
}
```

Cada componente de React tendrá lo que llamamos **props**, una abreviatura de
propiedades. Son elementos que podemos pasar al componente en el momento de su
creación y necesitaremos después para construirlo.

En este caso, queremos que nuestro componente reciba una propiedad _contenido_,
que será de tipo _string_; será el texto que mostre nuestro componente.

```typescript
const MiTexto = (props: PropsTexto) => {
```

Hay varias formas de crear un componente para React Native, la más simple es
crear una función que reciba un conjunto de propiedades, o **props**. En este
caso, hemos definido la función como una [lambda][3], pero podríamos haber usado
una función normal.

En los argumentos de la función, `(props: PropsTexto)`, definimos que aceptamos
`props` que además será de tipo `PropsTexto`. Esto nos ayudará en el
autocompletado del editor y también se asegurará que no nos falta ninguna
propiedad a la hora de crear nuestro componente.

En este caso, si queremos crear un componente `MiTexto` pero no le pasamos la
propiedad `contenido` o no es de tipo `string`, el editor nos mostrará un error.

```typescript
    return <Text>{props.contenido}</Text>
```

Lo que devuelve la función son las "instrucciones" para construir la vista de
nuestro componente. En este ejemplo, lo que vamos a devolver es un elemento de
tipo [`Text`][2] que muestra un texto, en concreto, la propiedad _contenido_.

Aquí podemos apreciar que hay una sintaxis rara que no encaja ni en JavaScrpt ni
en TypeScript. La parte de las `<Etiquetas>` que es más parecida a XML o HTML.
Es una sintaxis llamada JSX que permite la creación de este tipo de objetos.

Dentro de las etiquetas `<Text>` hemos abierto llaves `{ }` **para poder poner
nuestra variable** `props.contenido`. En la sintaxis JSX, si queremos **insertar
una variable**, o cualquier **expresión**, tenemos que hacerlo dentro de llaves
para que entienda que no es JSX, sino código normal.

```typescript
export default MiTexto;
```

Esta última línea no es específica de React Native. Sirve para poder importar
nuestro componente desde otro archivo para poder usarlo.

## Ya está

Con eso concluimos la creación de nuestro primer componente para React Native.
En las siguientes guías veremos como usarlo.

[1]: https://github.com/marionauta/notas-react-native/blob/master/typescript/configuracion.md
[2]: https://facebook.github.io/react-native/docs/text.html
[3]: https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Funciones/Arrow_functions
