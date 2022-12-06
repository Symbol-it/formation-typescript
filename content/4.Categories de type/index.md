# Les differents types

## JS

`number` `string` `boolean` `null` `undefined`

## Objects

```ts
let car = {
  constructeur: "Renault",
  modele: "Twingo",
  annee: 2022,
};
```

```ts
let car: {
  constructeur: string;
  modele: string;
  annee: number;
} = {
  constructeur: "Renault",
  modele: "Twingo",
  annee: 2022,
};
```

On definit un object par:

- le nom des proprietes
- le type des proprietes

```ts
function printCar(car: {
  constructeur: string;
  modele: string;
  annee: number;
}) {
  console.log(`${car.constructeur} ${car.modele} (${car.annee})`);
}
```

### propriete optionelle

On peut utiliser l'operateur `?` pour declarer une propriete comme etant optionelle.

```ts
function printCar(car: {
  constructeur: string;
  modele: string;
  annee: number;
  puissanceRecharge?: number; // number | undefined
}) {
  let str = `${car.constructeur} ${car.modele} (${car.annee})`;

  if (typeof car.puissanceRecharge !== "undefined") {
    str += ` ${car.puissanceRecharge}`;
  }

  console.log(str);
}
```

### Index signatures

Utile pour la definition de dictionnaire (des valeurs de meme type, recuperees via une clef)

```ts
const phones = {
  home: { country: "+1", area: "211", number: "652-4515" },
  work: { country: "+1", area: "670", number: "752-5856" },
  fax: { country: "+1", area: "322", number: "525-4357" },
};
```

```ts
const phones : {
  [k: string]: {
    country: string
    area: string
    number: string
  }
} = {};

phones.fax
```

## Arrays

Rien de plus facile que de declarer un tableau, il suffit d'ajouter `[]` apres le type.

```ts
const extensions = ["js", "ts"];
```

## Tuples

Les tuples, c'est comme des tableaux, dans lesquels l'ordre de chaque elements a un sens

```ts
//              [Annee, Marque,   Modele  ]
const voiture = [2002, "Renault", "Twingo"];
```

Si on laisse le compilateur faire, ici, on n'obtient pas ce que le veut

```ts
const voiture: [number, string, string] = [2002, "Renault", "Twingo"];
```

ATTENTION cependant, TS ne s'en sors pas tres bien sur les contraintes de tailles (en partie car il reutilise les tableaux JS)

```ts
const nombres: [number, number] = [2002, 2003, 2234];
```

```ts
const nombres: [number, number] = [2002, 2003];
nombres.push(55);
nombres.pop();
nombres.pop();
nombres.pop();
```
