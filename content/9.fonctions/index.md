# Fonctions

## Callable types

On peut utiliser les `types alias` ou les `interface` pour decrire des type que l'on peut appeler, ou construire avec le mot clef `new`

```ts
interface Calculette {
  (x: number, y: number): number;
}

type TwoNumberCalc = (x: number, y: number) => number;

const add: TwoNumberCalc = (a, b) => a + b;

const sub: Calculette = (a, b) => a - b;
```

Si votre fonction ne retourne aucun resultat, il faut typer le resultat avec `void`. (evite de retourner `undefined` et ca informe l'utilisateur et le compilateur que le resultat doit etre ignore)

### constructor

```ts
interface DateConstructor {
  new (value: number): Date;
}

let myConstructor: DateConstructor = Date;
const d = new MyDateConstructor();
```

## Function overloads

```html
<iframe src="https://example.com" />
<!-- // -->
<form>
  <input type="text" name="name" />
  <input type="text" name="email" />
  <input type="password" name="password" />
  <input type="submit" value="Login" />
</form>
```

```ts
type FormSubmitHandler = (data: FormData) => void
type MessageHandler = (evt: MessageEvent) => void

function handleMainEvent(
  elem: HTMLFormElement,
  handler: FormSubmitHandler
)
function handleMainEvent(
  elem: HTMLIFrameElement,
  handler: MessageHandler
)
function handleMainEvent(
  elem: HTMLFormElement | HTMLIFrameElement,
  handler: FormSubmitHandler | MessageHandler
) {}

const myFrame = document.getElementsByTagName("iframe")[0]

const myFrame: HTMLIFrameElement
const myForm = document.getElementsByTagName("form")[0]

const myForm: HTMLFormElement
handleMainEvent(myFrame, (val) => {

function handleMainEvent(elem: HTMLIFrameElement, handler: MessageHandler): any (+1 overload)
})
handleMainEvent(myForm, (val) => {

function handleMainEvent(elem: HTMLFormElement, handler: FormSubmitHandler): any (+1 overload)
})
```
