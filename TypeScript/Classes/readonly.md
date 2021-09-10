## readonly properties

```tsx
class Person {
  public readonly name: string = "Mark";
  private readonly country: string = "Korea";

  public constructor(public _name: string, private age: number) {
    this.country = "Korea";
  }

  hello() {
    this.country = "China"; // Error
  }
}
```

→ `readonly` 키워드가 달려 있는 경우는 `public`, `private` 모두 값을 초기화되는 영역에서만 사용 가능

→ `constructor` 안에서는 값 변경 가능

→ 다른 메소드 안에서는 값을 바꿀 수 없도록 지정