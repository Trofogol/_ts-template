# TypeScript template project

Level: beginner

This is a template file layout for TypeScript project. It contains prepared 
`.gitignore` and `tsconfig.json` files to jumpstart any development.

> Note: as you will add 3rd party modules (libraries), `package.json` and 
`package-lock.json` files should appear. They contain list of all external 
dependencies of your project. Make sure to commit them to your repo as well.

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

Feel free to play around with `tsconfig.json` ([docs](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)),
 rename your folders or change compiler behaviour. It is your project now.

It is recommended to initialize your project as a module (set name, version, 
dependencies etc.). To do it, run
```
npm init
```
An interactive creation of `package.json` file will be started. Fill out prompted 
fields, and you are good to go.

More iformation about `package.json` fields can be found in 
[the official docs](https://docs.npmjs.com/creating-a-package-json-file).

### Modules (libraries)

Refer to [the documentation](https://www.typescriptlang.org/docs/handbook/2/modules.html) 
for more information about modules. Short version is described below.

#### External modules

1. Install a module you want to use (it will appear in `node_modules` 
directory)

```
npm install module-name
```

2. Import it to your code (any of `.ts` file):

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
step; `[module-]alias` is an alias you are free to name as you please; 
`specificSomething1` is the exact name of exported object/function/constant/etc
described in module source code

#### Local modules

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