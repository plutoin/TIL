## 호이스팅(Hoisting)

함수 선언부가 유효 범위 최상단으로 끌어올려지는 현상
> 함수의 이름만으로 로직을 추측하여 호출할 수 있으므로 함수를 최하단에다 주로 작성하고 위에서는 주로 호출 가능

```jsx
const a = 7

double()

const double = function () {
  console.log(a * 2)
}
```

→ TypeError 발생, double 함수가 만들어지기 전에 호출했기 때문

```jsx
const a = 7

double()

function double () {  // 함수 선언
  console.log(a * 2)
}
```

→ 호이스팅 발생으로 함수 실행되어 14 반환