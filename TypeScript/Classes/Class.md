## Class
- object를 만드는 blueprint(청사진, 설계도)
- 클래스 이전에 object를 만드는 기본적인 방법은 function
- JavaScript에도 class es6부터 사용 가능
- OOP를 위한 초석
- TypeScript에서는 클래스도 사용자가 만드는 타입의 하나


### 클래스 사용
- `class` 키워드를 이용하여 클래스 생성
- `class` 이름은 보통 대문자 사용
- `new` 이용하여 `class`를 통해 `object` 생성 가능
- `constructor`이용하여 `object`를 생성하면서 값 전달 가능
- `this` 를 이용해서 만들어진 `object`를 가리킬 수 있음
- JS 로 컴파일되면 es5 의 경우 `function`으로 변경된다.

```tsx
class Person {}

const p1 = new Person();

console.log(p1);
```

→ `npx tsc`로 컴파일한 뒤 `node 파일명.js`로 실행하면 `Person {}` 출력

<br/>

현재 `tsconfig.json` 에서 es5를 타겟팅 중이기 때문에 js 파일에서 class를 다른 것으로 변환함

```jsx
// js
"use strict";
var Person = /** @class */ (function () {
    function Person() {
    }
    return Person;
}());
var p1 = new Person();
console.log(p1);
```

<br/>

`tsconfig.json`에서 `"target": "es6"`으로 변경 후 컴파일

```jsx
// js
"use strict";
class Person {
}
const p1 = new Person();
console.log(p1);
```

<br/>

class 밖의 데이터를 class 안으로 넣어서 사용하고 싶을 경우

```tsx
const p1 = new Person("Mark");
```

→ class 안에서 받는 코드가 없기 때문에 오류

`constructor` 이용하여 `object`를 생성하면서 값 전달 가능  
`this` 를 이용해서 만들어진 `object`를 가리킬 수 있음

```tsx
class Person {
  constructor(name: string) {
    this.name = name;
  }
}
```

→ `name`이라는 것을 어디선가 선언하지 않았기 때문에 오류 발생

<br/>

`name`을 property로 쓰겠다고 선언

```tsx
class Person {
  name;
  constructor(name: string) {
    this.name = name;
  }
}
```

→ `Person`이라는 클래스 생성

→ object가 만들어졌을 때 `.name`이라는 property를 가지게 되며 그 실제 값은 생성자 함수가 받아 `name`을 형성

<br/>

전체 코드

```tsx
class Person {
  name;
  constructor(name: string) {
    this.name = name;
  }
}

const p1 = new Person("Mark");

console.log(p1);
```

결과: `Person { name: 'Mark' }` 출력