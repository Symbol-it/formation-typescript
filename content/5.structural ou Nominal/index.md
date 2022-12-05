# Structural ou Nominal

## Les differents systemes de type

En quoi Typescript est-il different de Java et de Javascript

## Type checking

Ce type est-il compatible ou equivalent ?

Le type checking est utile pour savoir si on peut utiliser cette variable pour cet appel de methode, ou si cette affectation est possible etc etc

```ts
function foo(x) {
  // ... mystery code ...
}
//
// TYPE CHECKING
// -------------
// Is `myValue` type-equivalent to
//     what `foo` whats to receive?
foo(myValue);
```

```ts
// is the value y holds type-equivalent to what `x` allows?
x = y;
```

```ts
const myStrings = ["a"];
/// ---cut---
function bar(): string[] {
  // ...mystery code that might return early...
  //
  //
  // TYPE CHECKING
  // -------------
  // Is `myStrings` type-equivalent to
  //     what `bar` states it will return?
  return myStrings;
}
```

## Static ou dynamique

Ca depend de quand/comment est fait le type checking (runtime ou compile time)

Typescript est de type static comme Java ou C# ou C++

A l'inverse Javscript, php sont de type dynamique

## Nominal ou structurel

Les systemes de types "Nominaux" utilisent les noms ... Comme en java

Pour comparer l'equivalence de type, on va comparer les noms des types.

Typescript lui repose sur un systeme Structurel. Il utilise la structure, la forme des objets.

```ts
class Car {
  make: string;
  model: string;
  year: number;
  isElectric: boolean;
}

class Truck {
  make: string;
  model: string;
  year: number;
  towingCapacity: number;
}

const vehicle = {
  make: "Honda",
  model: "Accord",
  year: 2017,
};

function printCar(car: { make: string; model: string; year: number }) {
  console.log(`${car.make} ${car.model} (${car.year})`);
}

printCar(new Car()); // Ok
printCar(new Truck()); // Ok
printCar(vehicle); // Ok
```

### Une histoire de canard

Si ca ressemble a un cannard, que ca nage comme un canard et que ca cancane comme un canard alors c'est "propablement" un canard
