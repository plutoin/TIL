## constructor & initialize
- 생성자 함수 없으면 디폴트 생성자 호출됨
- 프로그래머가 만든 생성자가 하나라도 있으면 디폴트 생성자는 사라짐
- `strict` 모드에서는 프로퍼티를 선언하는 곳 또는 생성자에서 값을 할당해야 함
- 프로퍼티를 선언하는 곳 또는 생성자에서 값을 할당하지 않는 경우에는 `!` 를 붙여서 위험을 표현
- 클래스의 프로퍼티가 정의되어 있지만 값을 대입하지 않으면 `undefined`
- 생성자에는 `async` 를 설정할 수 없음

<br/>

Person 클래스 생성

```tsx
class Person {
  name: string;
  age: number;
}
```

→ class 내에서 `name`에 값을 할당한다든지 초기화한 전적이 없으므로 에러

<br/>

값 할당 후 컴파일 및 출력

```tsx
class Person {
  name: string = "Mark";
  age: number;
}

const p1 = new Person();
console.log(p1);
```

→ `Person { name: 'Mark' }` 출력

<br/>


프로그래머가 만든 생성자가 하나라도 있으면 디폴트 생성자는 사라짐

```tsx
class Person {
  name: string = "Mark";
  age: number;
}

const p1: Person = new Person();
console.log(p1); // Person1 {}
console.log(p1.age);
```

→ `class`로부터 `new`를 했기 때문에 p1은 Person으로부터 만들어진 object이므로 타입이 클래스 이름인 Person

→ 그러므로 p1.age에 커서를 올렸을 때 Person에서 지정한 타입인 number로 뜨게 됨

→ 그러나 컴파일 후 출력 시 `undefined`가 뜨게 됨

<br/>

해결 방법

`tsconfig.json` 파일에서 해당 옵션 켜 줌

```json
"strictNullChecks": true,
"strictPropertyInitialization": true,
```

```tsx
class Person {
  name: string = "Mark";
  age: number;
}

const p1: Person = new Person();
console.log(p1);
p1.age = 39;
console.log(p1.age);
```

→ age에 값을 할당해 주어도 class에서는 읽지 못하므로 `age!: number;`로 작성

→ 그러나 `!` 사용할 때는 주의해서 사용할 것

<br/>

값 할당하는 방법

```tsx
class Person {
  name: string = "Mark";
  age: number;

  constructor(age: number) {
    this.age = age;
    // age: number; 와 같은 의미
  }
}

const p1: Person = new Person(39);
console.log(p1);
console.log(p1.age);
```

<img src="../images/5-1.png" width="400px" />

→ class 안에서 값을 할당하여도 되고 생성자 함수를 생성한 후 클래스 밖에서 new 통해 삽입하여도 됨

<br/>


여러 개의 값 할당하고 싶을 때

```tsx
class Person {
  name: string = "Mark";
  age: number;

  constructor(age: number) {
    this.age = age;
  }
	constructor(age: number) {
    this.age = age;
  }
}

const p1: Person = new Person(39);
const p2: Person = new Person();
console.log(p1);
console.log(p1.age);
```

→ 오버로딩을 사용할 수 없음

<br/>


클래스의 프로퍼티가 정의되어 있지만 값을 대입하지 않으면 `undefined` 특징 해당

```tsx
class Person {
  name: string = "Mark";
  age: number;

	// 수정
  constructor(age?: number) {
    if (age === undefined) {
      this.age = 20;
    } else {
      this.age = age;
    }
  }
}

const p1: Person = new Person(39);
const p2: Person = new Person();
console.log(p1);
console.log(p1.age);
```

→  값을 넣는 경우 39 출력, 안 넣을 경우 20으로 출력