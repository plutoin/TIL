## unknown

응용 프로그램 작성 시 모르는 변수의 타입을 묘사해야 하는 경우

- 동적 콘텐츠(예: 사용자로부터 또는 우리 API)의 모든 값을 의도적으로 수락하기를 원할 수 있음
- 컴파일러와 미래의 코드를 읽는 사람에게 이 변수가 무엇이든 될 수 있음으로 알려 주는 타입을 제공하기를 원하므로 `unknown` 타입 제공

#### 특징

- TypeScript 3.0 버전부터 지원
- `any`와 짝으로 `any`보다 Type-safe한 타입
    - `any`와 같이 아무거나 할당 가능
    - 컴파일러가 타입을 추론할 수 있게끔 타입의 유형을 좁히거나 타입을 확정해 주지 않으면 다른 곳에 할당할 수 없으며 사용 불가능
- `unknown` 타입을 사용하면 런타임 에러 줄일 수 있음
    - 사용 전 데이터 일부 유형의 검사를 수행해야 함을 알리는 API에 사용

```tsx
declare const maybe: unknown;

const aNumber: number = maybe;
// unknown은 number에 할당할 수 없다는 오류 발생

if (maybe === true) {
  const aBoolean: boolean = maybe;

  // const aString: string = maybe;  
  // maybe가 true이기 때문에 string에 할당 불가능
}

if (typeof maybe === 'string') {
  const aString: string = maybe;

  // const aBoolean: boolean = maybe;
  // aBoolean이 boolean 타입이므로 string에 할당 불가능
}
```

## never

#### 특징

- 모든 타입의 서브 타입이며 모든 타입에 할당 가능
- `never`에는 할당하는 것이 불가능(`any` 포함)
- 잘못된 타입을 넣는 실수를 막고자 할 때 사용

```tsx
function error(message: string): never {
  throw new Error(message);
}

function fail() {
  return error("failed");
}

function infiniteLoop(): never {
  while(true) {}
}
```

```tsx
let a: string = "hello";

if (typeof a != 'string') {
  a;
}
```

→ `string`이 들어가는 것을 막을 수 있음

<br/>

```tsx
type Indexable<T> = T extends string ? T & {[index: string]: any} : never;

type Objectindexable = Indexable<{}>;
```

→ T가 `string`이면 T를 `{[index: string]: any}`로 만들어서 내보내고 아닐 경우 `never`로 인해 실행하지 않음

## void

아무것도 하지 않는 타입

```tsx
function returnVoid(message: string) {
  console.log(message);
  return;
}

const r = returnVoid('리턴이 없음');
// r의 타입은 void
```

<br/>

- `undefined`는 할당 가능

```tsx
function returnVoid(message: string): void {
  console.log(message);
  return undefined;
}

const r = returnVoid('리턴이 없음');
// r의 타입은 void
```