## TypeScript Types vs JavaScript Types

#### TypeScript

- Static Types

    : 개발하는 중 타입 체크

#### JavaScript Types

- Dynamic Types

    : 개발 중에는 알 수 없고 런타임 시 타입 체크

```jsx
// JavaScript
function add(n1, n2) {
  if (typeof n1 !== 'number' || typeof n2 !== 'number') {
    throw new Error('Incorrect input!');
  }
  return n1 + n2;
}

const result = add(39, 28);
```

→ 실행 후에 에러가 있는지 없는지 알 수 있음

→ 때문에 `if`문의 조건으로 타입 식별

```tsx
// TypeScript
function add(n1: number, n2: number){
  return n1 + n2;
}

const result = add(39, 28);
```

→ 개발하며 타입이 일치하는지 확인 가능

### TypeScript 기본 제공 데이터 타입

- JavaScript 기본 자료형 포함 (superset)
- ECMAScript 표준에 따른 기본 자료형
    - Boolean
    - Number
    - Null
    - Undefined
    - Symbol (ECMAScript 6에 추가)
    - Array: object 형
- 프로그래밍을 돕는 타입들
    - Any, Void, Never, Unknown
    - Enum
    - Tuple: object 형

## Primitive Types

- `object`와 `reference` 형태가 아닌 실제 값을 저장하는 자료형

- `Primitive` 타입의 내장 함수를 사용 가능한 것은 JS 처리 방식 때문

### 종류

- boolean
- number
- string
- symbol (ES2015)
- null
- undefined

리터럴 값으로 `Primitive` 타입의 서브 타입을 나타낼 수 있다

```tsx
true;
'hello';
3.14;
null;
undefined;
```

<br/>

래퍼 객체로도 만들 수 있음

→ `Primitive` 타입이 아닌 `object` 형

→ 이러한 방법으로 사용하는 것을 권장하지 않음

```tsx
new Boolean(false); // typeof new Boolean(false) : 'object'
new String('world'); // typeof new String('world'): 'object'
new Number(42); // typeof new Number(42) : 'object'
```

<br/>

TypeScript의 핵심 `Primitive Types`는 모두 소문자

- `Number`, `String`, `Boolean`, `Symbol`, `Object` 유형은 `Primitives`를 나타내지 않으며 타입으로 사용해서는 안 됨
- 래퍼 객체 만들 때 사용
- 잘못된 예시

```tsx
function reverse(s: String): String {
  return s.split("").reverse.join("");
}

reverse("hello world");
```

- 올바른 예시

```tsx
function reverse(s: string): string {
  return s.split("").reverse.join("");
}

reverse("hello world");
```