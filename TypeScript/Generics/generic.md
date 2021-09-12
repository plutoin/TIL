## Generics, Any 차이

```tsx
function helloString(message: string): string {
  return message;
}

function helloNumber(message: number): number {
  return message;
}

// 더 많은 반복 함수

function hello(message: any): any {
  return message;
}

console.log(hello("Mark").length);
console.log(hello(39).length);
```

→ 컴파일에는 문제가 없지만 런타임에는 `undefined`

<br/>

들어가는 타입을 변수로 바꾸어 리턴 타입과 연관지어 사용하는 것이 `Generic`

```tsx
function helloGeneric<T>(message: T): T{
  return message;
}

console.log(helloGeneric("Mark"));
// message의 타입을 T라고 지정
// Mark가 함수에 들어가게 될 경우 타입은 string, T가 string이 됨
// message를 리턴하면 message의 리턴 타입 역시 T, string이 됨
console.log(helloGeneric(39));
// 리턴 타입 number
console.log(helloGeneric(true));
// 리턴 타입 boolean
```

`any`: 모든 것을 받아 모든 것으로 리턴하므로 동적으로 변하는 타입을 리턴 불가능 

`generic`: 타입으로 된 연산 가능

<br/>

## Generics Basic

Generic 타입을 쓰지 않으면 T를 추론

Generic 타입을 쓰면 T를 검증

```tsx
function helloBasic<T>(message: T): T {
  return message;
}

helloBasic<string>("Mark");
// function helloBasic<string>(message: string): string
helloBasic(36);
// function helloBasic<36>(message: 36): 36
```

→ <> 안에 타입을 넣고 사용할 경우 그 타입으로 리턴

→ 타입을 넣지 않고 값만 넣을 경우 그 값을 타입으로 인식, T가 추론됨

<br/>

타입 여러 개 사용할 경우

```tsx
function helloBasic<T, U>(message: T, comment: U): T {
  return message;
}

helloBasic<string, number>("Mark", 39);
// function helloBasic<string, number>(message: string, comment: number): string
helloBasic(36, 39);
// function helloBasic<36, number>(message: 36, comment: number): 36
```

<br/>

## Array & Tuple

```tsx
function helloArray<T>(messages: T[]): T {
  return messages[0];
}

function helloTuple<T, K>(messages: [T, K]): T {
  return messages[0];
}

console.log(helloArray(['Hello', 'World'])); 
// string[]
console.log(helloArray(['Hello', 1])); 
// Array<string | number>의 union 타입

console.log(helloTuple(['Hello', 'World'])); 
// [string, string]
console.log(helloTuple(['Hello', 1])); 
// [string, number]

// console.log(helloTuple(['Hello', 'world', 1])); 
// Error
```

<br/>

## Function

```tsx
type HelloFunctionGeneric1 = <T>(message: T) => T;

const helloFunction1: HelloFunctionGeneric1 = <T>(message: T): T => {
  return message;
};

interface HelloFunctionGeneric2 {
  <T>(message: T): T;
}

const helloFunction2: HelloFunctionGeneric2 = <T>(message: T): T => {
  return message;
}
```

<br/>

## Class

```tsx
class Person<T> {
  private _name: T;

  constructor(name: T) {
    this._name = name;
  }
}

new Person("Mark");
// new Person<string>(3); (X)
```

```tsx
class Person<T, K> {
  private _name: T;
  private _age: K;

  constructor(name: T, age: K) {
    this._name = name;
    this._age = age;
  }
}

new Person("Mark", 39);
// new Person<string>(39); (X)
// new Person<string, number> ("Mark", "age");
```

<br/>

## extends

```tsx
class Person6<T extends string | number> {
  private _name: T;

  constructor(name: T) {
    this._name = name;
  }
}

new Person6('Mark');
new Person6(38);
// new Person6(true); // T 가 string 또는 number 를 상속받기 때문에 boolean 은 X
```

→ T는 `string | number`의 `union` 타입의 상속을 받음

→ T는 `string` 혹은 `number` 타입만 가질 수 있음

<br/>

## keyof & type lookup system

```tsx
interface IPerson {
  name: string;
  age: number;
}

const person: IPerson = {
  name: "Mark",
  age: 39
};

function getProp(obj: IPerson, key: "name" | "age"): string | number {
  return obj[key];
}

function setProp(
  obj: IPerson,
  key: "name" | "age",
  value: string | number
): void {
  obj[key] = value;
}
```

→ `key: "name" | "age"`  와 `string | number` 가 연관성을 가지면서 오류를 발생하게 되는데, 이때 사용하는 것이 `keyof`

<br/>

`keyof`: 개체에 사용할 경우 결과물로 타입을 반환하게 되는데 그 타입의 이름은 `key`의 이름으로 된 문자열의 union type으로 생성

```tsx
type Keys = keyof IPerson;

const keys: Keys = "age";
```

위의 코드를 아래처럼 생성

```tsx
// IPerson[keyof IPerson]
// => IPerson["name" | "age"]
// => IPerson["name"] | IPerson["age"]
// => string | number

function getProp(obj: IPerson, key: keyof IPerson): IPerson[keyof IPerson] {
  return obj[key];
}
```

→ `IPerson`과 `keyof IPerson`을 이용하여 그 관계를 특정한 타입으로 지정해 주어야 하기 때문에 제네릭 사용 필요

<br/>

제네릭 추가

```tsx
function getProp<T>(obj: T, key: keyof T): T[keyof T] {
  return obj[key];
}
```

<br/>

추가 정의

```tsx
function getProp<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}
```

→ `K extends keyof T`: K는 `name` 혹은 `age`로만 받을 수 있음

→ `key`의 값에 따라 K가 `name` 혹은 `age` 중 맞는 것으로 바로 바뀜

<br/>

결과

```tsx
getProp(person, "name");  // string
getProp(person, "age");  // number
// getProp(person, "age1");  // Error 발생, keyof IPerson에 해당하는 것이 아님
```

→ 컴파일 타임에 바로 오류 알 수 있으므로 편리함

<br/>

전체 코드

```tsx
interface IPerson {
  name: string;
  age: number;
}

const person: IPerson = {
  name: "Mark",
  age: 39
};

function getProp<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

getProp(person, "age");  // number

function setProp<T, K extends keyof T>(obj: T, key: K, value: T[K]): void {
  obj[key] = value;
}

setProp(person, "name", "Anna");
```