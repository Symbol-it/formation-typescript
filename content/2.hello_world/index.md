---
title: "Hello world"
description: ""
---

# Hello Typescript World

## Instalation - premier projet

package.json

```json
{
  "name": "hello-typescript",
  "license": "NOLICENSE",
  "version": "0.0.1",
  "devDependencies": {
    "typescript": "^4.9.3"
  },
  "scripts": {
    "dev": "tsc --watch --preserveWatchOutput"
  }
}
```

tsconffig.json

```json
{
  "compilerOptions": {
    "outDir": "dist",
    "target": "ES3"
  },
  "include": ["src"]
}
```

hello-world.ts

```ts
/**
 * Create a promise that resolves after some time
 * @param n number of milliseconds before promise resolves
 */
function timeout(n: number) {
  return new Promise((res) => setTimeout(res, n));
}

/**
 * Add three numbers
 * @param a first number
 * @param b second
 */
export async function addNumbers(a: number, b: number) {
  await timeout(500);
  return a + b;
}

//== Run the program ==//
(async () => {
  console.log(await addNumbers(3, 4));
})();
```

Credit code - Mike North - ts-fundamentals-v3

npm

## Javascript et type de module

Le tsconfig.json permet de configurer vers quel niveau de Javascript le compilateur doit aller, mais aussi de definir quel type de module utiliser, ES pour les navigateurs, CommonJS pour node.

## output

Tsconfig.json permet aussi de specifier un repertoire de sortie "outDir", si on ne le specifie pas, les fichiers sont generes au meme niveau que leurs equivalents TS.

Je conseille de toujours definir un repertoire de sortie.

## Evolution au fil des versions de JS/ES

Dans l'exemple on utilise async / await ainsi que des promesses, pourtant on transpile vers ES3, on voit donc que TSC genere des polyfills pour que le code fonctionne (j'avais dit lisibilite ????)

Essayez de changer le niveau de JS avec en modifiant la propriete target du tsConfig
