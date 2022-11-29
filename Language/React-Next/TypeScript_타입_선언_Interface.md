TypeScript 타입 선언 Interface 기본 문법

```
interface Animal {
    name: string
    age: number
}

const cat: Animal = {
    name: "fillwoo",
    age: 3
}

```


선택적 프로퍼티 ?:

```
interface Animal {
    name: string
    age?: number
}

const cat: Animal = {
    name: "fillwoo",
    age: 3
}

const dog: Animal = {
    name: "coco"
}
```


인터페이스 중복

```
interface Animal {
    name: string
}

interface Animal {
    age: number
}

const cat: Animal = {
    name: "fillwoo",
    age: 3
}
```


인터페이스 확장

```
interface Animal {
    name: string
}

interface Mammal extends Animal {
    age: number
}

const cat: Mammal = {
    name: "fillwoo",
    age: 3
}
```