## ES6 Classes

```jsx
const heropy = {
  name: 'Heropy',
  normal: function () {
    console.log(this.name)
  },
  arrow: () => {
    console.log(this.name)
  }
}

heropy.normal()
heropy.arrow()
```

일반 함수를 사용할 때 콜론 기호와 함꼐 `function` 키워드를 삭제해도 일반 함수로 사용할 수 있음

<br/>

수정

```jsx
const heropy = {
  name: 'Heropy',
  normal() {
    console.log(this.name)
  },
  arrow: () => {
    console.log(this.name)
  }
}

heropy.normal()
heropy.arrow()
```

자바스크립트는 프로토타입 기반의 프로그래밍 언어인데, 더 안정적이고 신뢰도가 높은 객체 지향 프로그래밍 언어들의 영향을 받아서 클래스 개념을 흉내낸 새로운 문법을 `ES6 Class` 에서 제공하기 시작

- 이전 클래스 작성 코드

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

console.log(heropy)
console.log(amy.getFullName())
console.log(neo.getFullName())
```

- ES6 Class

```jsx
class User {
  constructor(first, last) {
    this.firstName = first
    this.lastName = last
  }
  getFullName() { // prototype을 사용하지 않고 동일 기능 제공
    return `${this.firstName} ${this.lastName}`
  }
}

const heropy = new User('Heropy', 'Park')
const amy = new User('Amy', 'Clarke')
const neo = new User('Neo', 'Smith')

console.log(heropy)
console.log(amy.getFullName())
console.log(neo.getFullName())
```