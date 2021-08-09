## 생성자 함수(prototype)

```jsx
const heropy = {
  firstName: 'Heropy',
  lastName: 'Park',
  getFullName: function () {
    return `${this.firstName} ${this.lastName}`
  }
}
console.log(heropy.getFullName())

const amy = {
  firstName: 'Amy',
  lastName: 'Clarke',
  getFullName: function () {
    return `${this.firstName} ${this.lastName}`
  }
}
console.log(amy.getFullName())

const neo = {
  firstName: 'Neo',
  lastName: 'Smith',
  getFullName: function () {
    return `${this.firstName} ${this.lastName}`
  }
}
console.log(neo.getFullName())
```

<img src="../images/4-1-1.png" width="200px" />

간단한 코드가 아닌 규모가 큰 로직에서는 `getFullName` 함수처럼 내용이 똑같은 함수들을 반복해서 사용하면 효율(메모리)이 떨어짐  
이때 사용하는 것이 클래스
  
<br/>

```jsx
function user (first, last) {
  this.firstName = first
  this.lastName = last
}

const heropy = new user('Heropy', 'Park') // 생성자 함수
const amy = new user('Amy', 'Clarke')
const neo = new user('Neo', 'Smith')

console.log(heropy)
console.log(amy)
console.log(neo)
```

`const heropy = {}` : 리터럴 방식

인스턴스: `new` 라는 키워드를 통해 생성자 함수로 실행한 결과를 반환하여 할당된 변수(heropy, amy, neo)

<br/>

```jsx
function User (first, last) {
  this.firstName = first
  this.lastName = last
}
User.prototype.getFullName = function () {
  return `${this.firstName} ${this.lastName}`
}

const heropy = new User('Heropy', 'Park')
const amy = new User('Amy', 'Clarke')
const neo = new User('Neo', 'Smith')

console.log(heropy.getFullName())
console.log(amy.getFullName())
console.log(neo.getFullName())
```

<img src="../images/4-1-1.png" width="200px" />

<br/>

#### 기존 방식과 다른 점
- `prototype` 키워드 사용하여 로직을 통일화한 후 메모리 효율적으로 관리
- 아래에 몇 개의 객체(heropy, amy, neo)를 생성하든 함수는 한 번 생성으로 여러 번 사용 가능

→ 때문에 자바스크립트를 프로토타입 기반의 프로그래밍 언어라고 부르기도 함

#### 자바스크립트 클래스
- `prototpye`을 사용하여 `new` 키워드와 함께 생성자 함수로 인스턴스를 만들어 내는 것
- 기존 다른 프로그래밍 언어의 클래스와는 다른 개념

<br/>

생성자로 사용되는 함수는 `CamelCase`가 아닌 `PascalCase`로 작성해야 함
`user → User`

ex) `Swiper`가 `CamelCase`로 생성된 것을 보고 생성자 함수라는 것을 알 수 있음

```jsx
new Swiper('.notice-line, .swiper-container,
	direction: 'vertical',
	autoplay: true,
	loop: true
})
```