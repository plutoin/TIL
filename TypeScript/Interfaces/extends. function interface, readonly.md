## extends

인터페이스끼리 상속

```tsx
interface IPerson2 {
  name: string;
  age?: number;
}

interface Korean extends IPerson2 {
  city: string;
}

const k: Korean = {
  name: '이웅재',
  city: '서울'
  // age는 넣어도 되고 빼도 됨
};
```

<br/>

## function interface

함수를 인터페이스로 만들어 내기

```tsx
interface HelloPerson {
  // (name: string, age: number): void;
  (name: string, age?: number): void;
}

let helloPerson: HelloPerson = function (name: string) {
  console.log(`안녕하세요! ${name} 입니다.`);
};

helloPerson('Mark'); // 안녕하세요! Mark 입니다.

/*
함수의 타입 체크는 할당할때가 아니라 사용할때 한다는 점을 명심
*/
```

→ `helloPerson`에 `HelloPerson` 타입을 지정한 후 안에 `string` 타입을 가지는 `name` 속성을 가지는 함수 생성

<br/>

오류 생기는 코드

```tsx
const helloPerson: HelloPerson = function (name: string, age: number) {
  console.log(`안녕하세요! ${name} 입니다.`);
}
```

→ `HelloPerson`의 `age`와 함수의 `age`가 대응하지 않음

→ `HelloPerson`의 타입은 `number | undefined`이므로 함수보다 큼

<br/>

## Readonly

한 번 생성 후 바뀌지 않아야 하는 값이라면 `readonly` 사용

```tsx
interface Person8 {
  name: string;
  age?: number;
  readonly gender: string;
}

const p81: Person8 = {
  name: "Mark",
  // age 생략 가능
  gender: "male"
};

p81.gender = "female";
```