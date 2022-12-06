# Classes

Typescript ajoute les concepts de `class fields` et `access modfier keyword` aux classes Javascript.

## class fields

```js
class Car {
  constructor(make, model, year) {
    this.make = make
    this.model = model
          
    Car.model: any
    this.year = year
  }
}
 
let sedan = new Car("Honda", "Accord", 2017)
sedan.activateTurnSignal("left") // not safe!
new Car(2017, "Honda", "Accord") // not safe!
```

Le fait de typer les classes permets d'ajouter de la securite

```ts
class Car {
  make: string
  model: string
  year: number
  constructor(make: string, model: string, year: number) {
    this.make = make
    this.model = model
          
(property) Car.model: string
    this.year = year
  }
}
 
let sedan = new Car("Honda", "Accord", 2017)

sedan.activateTurnSignal("left") // not safe!

new Car(2017, "Honda", "Accord") // not safe!
```

Ici en ajoutant les `types annotation` sur les membres de la classes ainsi que sur le constructeur, le copmpilateur peut nous aider dans l'utilisation de notre classe.


## modifier keywords

Typescript ajoute `public` `protected` `private` qui permettent de changer la visibilite des membres d'une classe.

`public` => everyone (c'est la valeur par defaut)
`protected` => l'instance (`this`) et les sous classes
`private` => seulement l`instance

```ts
class Car {
  public make: string
  public model: string
  public year: number
  protected vinNumber = generateVinNumber()
  private doorLockCode = generateDoorLockCode()
 
  constructor(make: string, model: string, year: number) {
    this.make = make
    this.model = model
    this.year = year
  }
 
  protected unlockAllDoors() {
    unlockCar(this, this.doorLockCode)
  }
}

class Sedan extends Car {
  constructor(make: string, model: string, year: number) {
    super(make, model, year)
    this.vinNumber
    this.doorLockCode
  }

  public unlock() {
    console.log("Unlocking at " + new Date().toISOString())
    this.unlockAllDoors()
  }
}

let s = new Sedan("Honda", "Accord", 2017)

s.make

s.vinNumber

s.doorLockCode

s.unlock()
```

*Attention, c'est juste a la compilation, une fois en JS c'est open bar*

`readonly`

```ts
class Car {
  public make: string
  public model: string
  public readonly year: number
 
  constructor(make: string, model: string, year: number) {
    this.make = make
    this.model = model
    this.year = year
  }
 
  updateYear() {
    this.year++
  }
}
```

une autre syntaxte est possible

```ts
class Car {
  constructor(
    public make: string,
    public model: string,
    public year: number
  ) {}
}
 
const myCar = new Car("Honda", "Accord", 2017)
myCar.make
```

Le constructeur est le suel autre endroit ou les `access modfiers` sont utilisable.

