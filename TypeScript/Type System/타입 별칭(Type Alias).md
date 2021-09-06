## 타입 별칭 (Type Alias)

- Interface와 유사
- Primitive, Union Type, Tuple, Function
- 기타 직접 작성해야 하는 타입을 다른 이름으로 지정할 수 있음
- 만들어진 타입의 `refer`로 사용하는 것이지 타입을 만드는 것은 아님

### Aliasing Primitive

```tsx
type MyStringType = string;

const str = 'world';

let myStr: MyStringType = 'hello';
myStr = str;

/* 별 의미가 없다 */
```

→ `string`을 MyStringType이라고 부르도록 지정

→ myStr은 MyStringType 타입으로 지정, 고로 `string` 타입이라는 뜻

### Aliasing Union Type

- 가장 많이 쓰이는 방법

```tsx
let person: string | number = 0;
person = 'Mark';

type StringOrNumber = string | number;

let another: StringOrNumber = 0;
another = 'Anna';

/*
1. 유니온 타입은 A 도 가능하고 B 도 가능한 타입
2. 길게 쓰는 걸 짧게
*/
```

→ person을 `string` 혹은 `number` 타입으로 지정

→ StringOrNumber를 `string` 혹은 `number` 타입을 가지는 별칭으로 지정

→ another이 StringOrNumber으로 지정되며 `string` 혹은 `number` 타입을 가지게 된다는 뜻

### Aliasing Tuple

```tsx
let person: [string, number] = ['Mark', 35];

type PersonTuple = [string, number];

let another: PersonTuple = ['Anna', 24];

/* 튜플 타입에 별칭을 줘서 여러군데서 사용할 수 있게 함 */
```

→ `union` 타입도 여러 번 반복해서 쓰기 힘드므로 PersonTuple로 별칭을 지정하여 사용 가능

### Aliasing Function

```tsx
type EatType = (food: string) => void;
```

→ 함수도 별칭을 지정하여 사용 가능