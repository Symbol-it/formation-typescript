# Top et Bottom type

## Top type

`any` => peut etre tout les types, et utilise tel quel (erreurs au runtime)

`unknow` => peut etre tous les types, mais on a besoin de type guard avant de pouvoir les utiliser.


## Bottom type

`never`=>


```ts
class Car {
  drive() {
    console.log("vroom")
  }
}
class Truck {
  tow() {
    console.log("dragging something")
  }
}
type Vehicle = Truck | Car
 
let myVehicle: Vehicle = obtainRandomVehicle()
 
// The exhaustive conditional
if (myVehicle instanceof Truck) {
  myVehicle.tow() // Truck
} else if (myVehicle instanceof Car) {
  myVehicle.drive() // Car
} else {
  // NEITHER!
  const neverValue: never = myVehicle
}
```