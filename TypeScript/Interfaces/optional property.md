## optional property

```tsx
interface Person2 {
  name: string;
  age?: number;
}

function hello2(person: Person2): void {
  console.log(`안녕하세요! ${person.name} 입니다.`);
}

hello2({ name: "Mark", age: 39 }); // 안녕하세요! Mark 입니다.
hello2({ name: "Anna" }); // 안녕하세요! Anna 입니다.
```

객체에 속성이 있을 수도 있고 없을 수도 있는 경우에는 `?` 사용

ex) `age?: number;`

<br/>

```tsx
interface Person3 {
  name: string;
  age?: number;
  [props: string]: any;
	// index 이름의 타입과 데이터의 타입
}

function hello3(person: Person3): void {
  console.log(`안녕하세요! ${person.name} 입니다.`);
}

const p31: Person3 = {
  name: 'Mark',
  age: 35,
};

const p32: Person3 = {
  name: 'Anna',
  systers: [
      'Sung',
      'Chan'
  ] // any와 대응되는 것
};

const p33: Person3 = {
  name: 'Bokdaengi',
  father: p31,
  mother: p32
};

hello3(p31); // 안녕하세요! Mark 입니다.
hello3(p32); // 안녕하세요! Anna 입니다.
hello3(p33); // 안녕하세요! Bokdaengi 입니다.
```