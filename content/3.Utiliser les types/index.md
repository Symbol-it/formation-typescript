# Les types en typescript

## Variables et valeur

### Inference de type

En js les variables sont declarees en utilisant les mots clefs `let` et `const`

```ts
let age = 6;

const REPONSE_UNIVERSELLE = 42;
```

Typescript est capable de reconnaitre (inferer) les types lors de **l'affectation**.

En typescript les variables naissent avec leur type. Il n'est pas possible de changer le type d'une variable apres son affectation.

Dans l'exemple le type de la variable `age` est infere en `number` et il n'est pas possible de lui afffecter une `string` par la suite.

```ts
let age = 6;

age = "ceci n'est pas possible";
```

### Literal type

Le comportement est le meme pour les `const`, mais cette fois typescript est capable d'aller un peu plus loin est d'etre plus specifique sur le type de `REPONSE_UNIVERSELLE`, pour le compilateur `42` est le type infere. Il s'agit d'un "literal type"

### any

Si on declare une variable sans lui afffecter une valeur, le compilateur la considerera du type `any`.

En typescript `any` est le type le plus flexible, c'est un peu comme une variable en JS.

### Type annotation

Le compilateur se debrouille tres bien pour ineferer le type des varibales, mais pour plus de securite, il est possible d'ajouter des "type annotation" lors de la declaration des variables

```ts
let age: number = 6;
```

### Arguments de fonction et valeur de retour

On peut aussi utiliser la syntaxe des "type annotation" pour specifier les types des arguments des fonctions, ainsi que pour la valeur de retrour

```js
function add(a, b) {
  return a + b;
}

const result = add(3, "4");
```

Ici les valeurs pour `a` et `b` peuvent etre des nombres, des strings ou meme un mix des deux (ou bien d'autre chose), typescript utilisera le type `any`, la methode va fonctionner dans la plupart des cas, ou alors il y aura une erreur au runtime.

`result` sera lui aussi inferer en type `any`.

```ts
const p = new Promise(result);
```

Voir le resultat [ici](https://www.typescriptlang.org/play?#code/GYVwdgxgLglg9mABAQwCaoBTIDSIEYCUiA3gFCKIBOAplCJUsogNT6kC+ppECAzlFWq8QAGwEBeFOgwBmbACIALPIJceYfogAOiSWGoB3RAAVKcALYxe1DDWFiCAbiA)

Normalement, pour creer une nouvelle `Promise`, on doit passer 2 `function` en parametre. ici le compilateur ne sais pas comment nous avertir, car nous passons un `any`.

En annontant les arguments et la valeur de retour de nos fonctions, on aide le compilateur dans son inference, mais aussi le developpeur dans l'utilisation et la lecture du code.

```ts
function add(a: number, b: number): number {
  return a + b;
}

const result = add(3, "4");

const p = new Promise(result);
```
