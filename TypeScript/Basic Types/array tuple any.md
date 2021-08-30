## Array

자바스크립트에서의 `Array`는 객체

#### 사용 방법

- Array<타입>
- 타입[]

```tsx
let list1: number[] = [1, 2, 3];  // 더 선호하는 방식

let list2: Array<number> = [1, 2, 3];

// 여러 타입을 한 배열에 사용할 때
let list3: (number | string)[] = [1, 2, 3, "4"];
```

→ 여러 타입을 한 배열에서 사용할 때는 `union` 타입 사용

<br/>

## Tuple

```tsx
let x: [string, number];

x = ["hello", 39];  // 순서와 타입, 길이까지 모두 일치해야 함

// x = [10, "Mark"];  // 오류

x[3] = "world";  // 없는 인덱스값 사용함
```

→ 순서와 타입, 길이까지 모두 일치해야 함

→ 때문에 `[10, "Mark"]`는 `[string, number]`로 지정해 둔 순서와 다르므로 오류

→ 없는 인덱스 번호에 값 삽입 시 오류, `[string, number]`에서는 인덱스 번호 1이 마지막이므로 2부터는 `undefined`

```tsx
const person: [string, number] = ["Mark", 39];

const [first, second, third] = person;
```

→ third는 들어갈 자리가 없으므로 오류

<br/>

## any

어떤 타입이어도 상관없는 타입

- 최대한 쓰지 않는 것을 권장
    - 컴팡리 타임에 타입 체크가 정상적으로 이루어지지 않기 때문
- 컴파일 옵션 중 `any`를 써야 하나 쓰지 않았을 때 오류를 뱉도록 하는 옵션 존재
    - `noImplicitAny`
- 타입 안전성은 TypeScript를 사용하는 주요 동기 중 하나이며 필요하지 않은 경우 `any`를 사용하지 않도록 해야 함

```tsx
function returnAny(message: any): any {
  console.log(message);
}

const any1 = returnAny('리턴은 아무거나');

any1.toString();  // 어떤 것이든 다 된다는 뜻
```

→ message라는 인자가 어떠한 타입이든 다 될 수 있다는 뜻을 가짐

<br/>

- 계속하여 개체를 통해 전파된다는 특징이 있음

```tsx
let looselyTyped: any = {};

const d = looselyTyped.a.b.c.d;
```

→ a, b, c, d 모두 `any`이며 마지막 d에 커서 올렸을 때 `any`로 확인됨

<br/>

누수를 막는 방식

```tsx
function leakingAny(obj: any) {
  const a = obj.num;
  const b = a + 1;
  return b;
}

const c = leakingAny({ num: 0 });  // c는 any로 확인됨
c.indexOf("0");  // 함수 내에 c가 없으므로 오류
```