## Type Annotation
: 변수에 특정 데이터 타입만이 할당될 수 있도록 정하는 것

```tsx
let a = 'Mark';
a = 39;
```

→ `a`에 최초 입력값이 Mark이므로 `String` 타입으로 지정됨

→ `a = 39;`에서 39는 `number`이므로 값 할당 불가능

```tsx
let a: number;
a = "Mark";
a = 39;
```

→ `a`의 타입을 `number`라고 지정

→ Mark는 `String`이므로 오류, 39가 입력됨

```tsx
function hellot(b: number) {

}
hello('Mark'); // error
hello(39);
```

→ 함수의 인자로 `number` 타입만 사용할 수 있음

→ Mark는 `String` 타입으로 불가능, 39는 `number`로 가능