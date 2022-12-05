# Interface et alias

## Type alias

Permet de donner un nom a un type.

```ts
type User = {
  name: string;
  email: string;
};

function printInfo(u: User) {
  console.log(u);
}
```

Permet de donner du sens a notre code.

On peut Import et Export

Le nom ne sert que pour donner du sens

```ts
type User = {
  name: string;
  email: string;
};

function printInfo(u: User) {
  console.log(u);
}

const fab = {
  name: "fabrice",
  email: "fabrice.claeys@symbol-it.fr",
  favoriteLangage: "Elm",
};

printInfo(fab); // Fonctionne parfaitement
```

On ne peut pas declarer 2 types avec le meme nom contrairement au

Exo : un peu de menage

```ts
function pileOuFace(): "pile" | "face" {
  if (Math.random() > 0.5) return "pile";
  return "face";
}

function getUserInfos():
  | ["error", Error]
  | ["success", { name: string; email: string }] {
  if (pileOuFace() === "pile") {
    return ["success", { name: "Joe", email: "test@test.com" }];
  } else {
    return ["error", new Error("Impossible de faire ce que je dois faire")];
  }
}
```

Il n'y a pas de notion d'heritage pour les types alias.
Il faut plutot les composer avec `&`, ou alors (je prefere) en declarer un nouveau.

```ts
type SpecialDate = Date & { getReason(): string };

const newYearsEve: SpecialDate = {
  ...new Date(),
  getReason: () => "Last day of the year",
};
```

Verifier l'autocompletion dans le playground

## Interface

Les interfaces sont un moyen de definir un "object type" (une instance d'une class qui ressemble a ...)

```ts
interface UserInfo {
  name: string;
  email: string;
}
```

### L'heritage, la POO

`extends`

`implements`

### Open interfaces

Celle la je l'avais pas vu venir ...

```ts
interface AnimalLike {
  isAlive(): boolean;
}
function feed(animal: AnimalLike) {
  animal.eat; // (method) AnimalLike.eat(food: any): void
  animal.isAlive; // (method) AnimalLike.isAlive(): boolean
}

// SECOND DECLARATION OF THE SAME NAME
interface AnimalLike {
  eat(food): void;
}
```

### Comment choisir ??

=> type alias => ma preference
=> interface
=> POO
=> permettre d'etendre

### Pour le fun

```ts
type NestedNumbers = number | NestedNumbers[];
```
