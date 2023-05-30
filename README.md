# TypeScript template project

This is a template file layout for TypeScript project. It contains prepared 
`.gitignore` and `tsconfig.json` files to jumpstart any development

## Build

### Prerequisites

In order to make it work, make sure you have prepared your environment tools

#### Node.js

Install Node.js tool to your system.

Use [official site](https://nodejs.org/en/download) to get it for your OS

You can safely skip `node-gyp` tool installation if you are not planning to 
develop and/or compile C/C++ written Node.js modules.

#### Typescript

This one is simple, get Node.js package (`-g` flag will install it globally)

```
npm install -g typescript
```

### Compile

This will compile (translate to JavaScript) a whole project

```
tsc
```

The JavaScript files will appear in `dist` directory

## Run

```
node dist/main.js
```

You can rename your main file as you please, just make sure you are working with 
`.ts` one

## Edit

If you got no errors after the run, you are ready to go. Edit the code in `src` 
directory, compile it and run from `dist` directory. Repeat until you are 
satisfied.

Refer to [the documentation](https://www.typescriptlang.org/docs/handbook/2/modules.html) 
for more information about modules. Short version is described below.

### External modules (libraries)

1. Install the module you want to use (it will appear in `node_modules` 
directory)

```
npm install module-name
```

2. Import to your code (any of `.ts` file):

- everything

```
import * as module-alias from 'module-name'
```

- only default export (can not exist at all)

```
import module-alias from 'module-name'
```

- specific parts that are designed to be exported

```
import specificSomething1, { specificSomething2 as alias } from 'module-name'
```

> `'module-name'` is the exact name of the installed module from the previous 
step; `alias` is an alias you are free to rename as you please; 
`specificSomething1` is the exact name of exported object/function/constant/etc
described in module

### Local modules (libraries)

Connect them as described above (step 2 only), just replace `'module-name'` with 
`'./relative/path/to/file.ts'`

The module itself should be a `.ts` file with `export` keyword(s) inside, e.g.

```
// @filename: maths.ts
export var pi = 3.14;
export let squareTwo = 1.41;
export const phi = 1.61;
 
export class RandomNumberGenerator {}
 
export function absolute(num: number) {
  if (num < 0) return num * -1;
  return num;
}
```

Full import should look like this

```
// @filename: main.ts
import * as math from "./maths.js";
 
console.log(math.pi);
const positivePhi = math.absolute(math.phi);
```