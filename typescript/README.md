# Usar TypeScript en tu proyecto

TypeScript permite que el autocompletado de tu editor de texto sea mejor,
al mismo tiempo te avisa si estás usando una función con unos parámetros
de un tipo incorrecto. Todo esto sin tener que ejecutar el código, las
comprobaciones se hacen en el momento de compilación.

**Nota**: en está guía usamos `yarn` como gestor de paquetes en lugar de
`npm`. La mayoría de comandos son equivalentes entre las dos herramientas.

## Configuraciones

### package.json

Lo primero es añadir las dependencias necesarias. Esta es una configuración básica:

```
{
  // ...
  
  "scripts": {
    // ...
    "tsc": "node_modules/typescript/bin/tsc"
  },
  
  "dependencies": {
    "react": "16.2.0",
    "react-native": "0.53.0",
  },
  
  "devDependencies": {
    "@types/react": "^16.0.38",
    "@types/react-native": "^0.52.9",
    "typescript": "^2.7.1"
  }
}
```
Y después ejecutar `yarn install`.

Esto nos instala las librerías de React Native así como las definiciones
de tipos relacionadas a estas. Si ya tenemos el compilador de TypeScript
instalado en el sistema podemos saltarnos la última línea, pero tenerlo
así nos permite compartir el proyecto con gente que no lo tenga instalado.

### tsconfig.json

```
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs", // valores posibles: none, commonjs, amd, system, umd, es2015 o ESNext.
    "jsx": "react", // importante
    
    "rootDir": "./src/",
    "outDir": "./lib/",
    
    "strict": true,
    "noUnusedLocals": true,
    "noImplicitReturns": true,
  }
}
```

Con esta configuración tendremos todos nuestros ficheros fuente `.ts`,
`.d.ts` y `.tsx` dentro de la carpeta `src` y tras la compilación se
generará la carpeta `lib` con los archivos `.js` que queremos para react.

La compilación no puede ser más fácil, simplemente hay que ejecutar
`yarn run tsc`. Si queremos que se compile cada vez que modifiquemos un
archivo (que viene muy bien para el _live reload_ de React Native) cambiamos
ligeramente el comando a `yarn run tsc -w`. La _w_ viene de _watch_.

### index.js

Por defecto el archivo principal del proyecto `index.js` se encuentra en
la carpeta raíz del proyecto. Tendremos que cambiar la segunda línea para
que pueda encontrar los archivos JavaScript generados:

```javascript
import App from './lib/App';
```

### Estructura del proyecto

Al final tendremos un proyecto con esta estructura más o menos:

```
- android
- ios
- lib
  - <archivos js>
- src
  - <archivos ts>
- index.js
- package.json
- tsconfig.json
```
