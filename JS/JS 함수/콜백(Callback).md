## 콜백 (Callback)

함수의 인수로 사용되는 함수  
ex) `setTimeout(함수, 시간)`에서 매개변수로 사용되는 함수가 콜백

특정 로직이 처리하는 데 시간이 많이 걸리는 경우 모든 처리 이후에 원하는 내용이 실행되도록 할 수 있음

코드 작성 시 특정한 실행 위치를 보장하는 방법으로 콜백 함수를 사용할 수 있음

```jsx
function timeout(cb) {
  setTimeout(() => {
    console.log('Heropy!')
    cb()
  }, 3000)
}
timeout(() => {
  console.log('Done!')
})
```

→ `timeout` 함수를 호출할 때 인수로 사용되는 익명 함수를 `cb`라는 매개변수로 들어가게 됨

→ 그 다음 차례대로 실행

→ 3초 후 Heropy! 글자가 뜨고 Done!이 뜨게 됨