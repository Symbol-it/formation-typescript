# Generics

Les generiques permettent de rendre nos types parametrable.



## Pourquoi ??

```ts
const phones: {
  [k: string]: {
    customerId: string
    areaCode: string
    num: string
  }
} = {}
 
phones.home
phones.work
phones.fax
phones.mobile
```

Ecrire une fonction qui permet de passer d'une liste a un dictionnaire

```ts
interface PhoneInfo {
  customerId: string
  areaCode: string
  num: string
}

const phoneList = [
  { customerId: "0001", areaCode: "321", num: "123-4566" },
  { customerId: "0002", areaCode: "174", num: "142-3626" },
  { customerId: "0003", areaCode: "192", num: "012-7190" },
  { customerId: "0005", areaCode: "402", num: "652-5782" },
  { customerId: "0004", areaCode: "301", num: "184-8501" },
]









function listToDict(
    list: PhoneInfo[],
    idGen: (arg: PhoneInfo) => string
) : {[k:string]: PhoneInfo} {

    const dict: {[k:string]: PhoneInfo} = {}

    list.forEach((elt) => {
        const key = idGen(elt)
        dict[elt] = elt
    })

    return dict
}

console.log(listToDict(phoneList, (item) => item.customerId)
```

Le probleme ici c'est que notre fonction ne fonctione que pour des `PhoneInfo`

Comment faire pour que ca fonctionne avec des listes d'autre type ?


`any` ???

```ts

function listToDict(
    list: any[],
    idGen: (arg: any) => string
) : {[k:string]: any} {

    const dict: {[k:string]: any} = {}

    list.forEach((elt) => {
        const key = idGen(elt)
        dict[elt] = elt
    })

    return dict
}
```