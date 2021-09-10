## Abstract Classes
- 완전하지 않은 클래스 표현
- `new`를 이용하여 객체 생성 불가능
- 상속 기능을 사용하여 완전한 객체로 바꿀 수 있음

```tsx
abstract class AbstractPerson {
  protected _name: string = "Mark";

  abstract setName(name: string): void;
}

// new AbstractPerson()

class Person extends AbstractPerson {
  setName(name: string): void {
    this._name = name;
  }
}

const p = new Person();
p.setName();
```