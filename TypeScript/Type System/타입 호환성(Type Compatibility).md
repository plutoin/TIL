## 타입 호환성(Type Compatibility)

서브타입

```tsx
// sub1 타입은 sup1 타입의 서브 타입
let sub1: 1 = 1;
let sup1: number = sub1;
sub1 = sup1;
// error: Type 'number' is not assignable to type '1'.

// sub2 타입은 sup2 타입의 서브 타입
let sub2: number[] = [1];
let sup2: object = sub2;
sub2 = sup2;
// error: Type '{}' is missing the following properties from type 'number[]': length, pop, push, concat, and 16 more.

// sub3 타입은 sup3 타입의 서브 타입
let sub3: [number, number] = [1, 2];
let sup3: number[] = sub3;
sub3 = sup3;
// error: Type 'number[]' is not assignable to type '[number, number]'. Target requires 2 element(s) but source may have fewer.
```

→ sub1은 리터럴 타입의 1, sup1은 `number` 타입으로 더 크므로 sup1 = sub1은 되지만 sub1 = sup1은 될 수 없음

→ sub2는 `number`로 된 `array`, sup2는 `object`
    `array`는 `object`의 서브 타입이므로 `object`가 더 큰 타입이므로 sub2 = sup2는 불가능

→ sub3은 `tuple` 타입, sup3은 `number`의 `array`로 sup3이 더 크므로 sub3 = sup3은 불가능

<br/>

```tsx
// sub4 타입은 sup4 타입의 서브 타입
let sub4: number = 1;
let sup4: any = sub4;
sub4 = sup4;

// sub5 타입은 sup5 타입의 서브 타입
let sub5: never = 0 as never;
let sup5: number = sub5;
sub5 = sup5;
// error: Type 'number' is not assignable to type 'never'.

class Animal {}
class Dog extends Animal {
	eat() {}
}

// sub6 타입은 sup6 타입의 서브 타입
let sub6: Dog = new Dog();
let sup6: Animal = sub6;
sub6 = sup6;
// error: Property 'eat' is missing in type 'SubAnimal' but required in type 'SubDog'.
```

### 1. 공변
- 같거나 서브 타입인 경우 할당이 가능

```tsx
// primitive type
let sub7: string = '';
let sup7: string | number = sub7;  // 더 넓은 개념

// object - 각각의 프로퍼티가 대응하는 프로퍼티와 같거나 서브타입이어야 한다.
let sub8: { a: string; b: number } = { a: '', b: 1 };
let sup8: { a: string | number; b: number } = sub8;

// array - object 와 마찬가지
let sub9: Array<{ a: string; b: number }> = [{ a: '', b: 1 }];
let sup9: Array<{ a: string | number; b: number }> = sub8;
```

### 2. 반병
- 함수의 매개변수 타입만 같거나 슈퍼타입인 경우 할당 가능

```tsx
class Person {}
class Developer extends Person {
  coding() {}
}
class StartupDeveloper extends Developer {
  burning() {}
}

function tellme(f: (d: Developer) => Developer) {}

// Developer => Developer 에다가 Developer => Developer 를 할당하는 경우
tellme(function dToD(d: Developer): Developer {
  return new Developer();
});

// Developer => Developer 에다가 Person => Developer 를 할당하는 경우
tellme(function pToD(d: Person): Developer {
  return new Developer();
});

// Developer => Developer 에다가 StartipDeveloper => Developer 를 할당하는 경우
tellme(function sToD(d: StartupDeveloper): Developer {
  return new Developer();
});
```

<br/>

`strictFunctionTypes` 옵션 켤 경우

- 함수를 할당할 시에 함수의 매개변수 타입이 같거나 슈퍼타입이 아닌 경우 에러를 통해 경고