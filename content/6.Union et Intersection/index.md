# Union et Intersection types

## Concept

Basiquement AND, OR

L'union est un OR pour les types

L'intersection lui est un AND

### Union

En typescript on decrit l'union avec le `|`

```ts
"success" | "error";
```

```ts
function pileOuFace(): "pile" | "face" {
  if (Math.random() > 0.5) return "pile";
  return "face";
}
```

Les unions types peuvent etre tres puissant combine avec les tuples pour modeliser par exemple le retour d'une fonction qui dois renvoyer plusieur resulats

```ts
function getUserInfos():
  | ["error", Error]
  | ["success", { name: string; email: string }] {}

const result = getUserInfos();

const [message, surprise] = result;
```

On s'amuse [ici](https://www.typescriptlang.org/play?#code/GYVwdgxgLglg9mABABxgGwKYHkQDECGEGAFAJQBciARKplYgD7XCEb0DeAUIojMIsQCy+KAAsAdACd8YACZwAtmUQA+RAAZxAVlKJJGKCElIa6NgG5ueg0ZMsiVSwF9Or0JFgJEAcwMBVAGcMSQBJMGA4ALJyKyYAbSpgyThJKgAaRABRSWTJAF1YxASAkAgiAID0xHZEMHwFDEoAqEkYMG9zRAwFfHQmlrbvRCc86tceHj4BWmw8VmUAXiXqGapdLgmJ-UNjIqoSsowKqvY6hvIqACk4Ngzu3rRKKigjqAABF+bxCEUqEaseE4umggmNNjxtrY9kkUlUwBgAO5ZHIpYhUEIKZCRAIwABGmEQsgwiBYMH0iCIiAAjiBiQArYnyGABEm9fRrAqbFyA1w-MDNawlNBQRALHz+IKhcKRMiWIA)

## Ok, mais comment on utilise ca ??

On a besoin de verifier dans lequel des cas on se trouve, en utilisant le meme principe que pour les proprietes optionelles

On utilise des "type guards" et des conditions

```ts
function getUserInfos():
  | ["error", Error]
  | ["success", { name: string; email: string }] {}

const result = getUserInfos();

const [message, surprise] = result;

if (surprise instanceof Error) {
  surprise;
} else {
  surprise;
}
```

Encore plus fort ?

```ts
function getUserInfos():
  | ["error", Error]
  | ["success", { name: string; email: string }] {}

const result = getUserInfos();

if (result[0] === "error") {
  result;
} else {
  result;
}
```

### Intersection type

J'avoue lui, je ne le connaissais pas

En typescript on decrit l'union avec le `&`

```ts
function makeWeek(): Date & { end: Date } {
  //⬅ return type

  const start = new Date();
  const end = new Date(start.valueOf() + ONE_WEEK);

  return { ...start, end }; // kind of Object.assign
}

const thisWeek = makeWeek();
thisWeek.toISOString();

thisWeek.end.toISOString();
```

J'ai du mal a voir quand, comment, pourquoi utiliser ca.
