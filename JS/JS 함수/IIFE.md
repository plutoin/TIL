## IIFE

### 즉시실행함수  
Immediately-Invoked Function Expression

이름이 없는 익명 함수를 바로 실행시키는 것

1. 소괄호로 함수를 감싸고 다른 소괄호를 뒤에 붙임

```jsx
const a = 7
function double () {
  console.log(a * 2)
}
double();

// 즉시실행함수
(function () {
  console.log(a * 2)
})();
```

→ 즉시실행함수 작성 시 앞 함수에 세미콜론(;) 붙일 것  
→ 즉시실행함수 마무리에도 붙일 것

2. 소괄호로 감싼 함수 내에서 마지막에 소괄호 하나 더 붙임(권장)

```jsx
(function () {
  console.log(a * 2)
}());
```