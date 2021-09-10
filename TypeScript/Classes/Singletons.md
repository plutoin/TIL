## Singletons

```tsx
class ClassName {}

const a = new ClassName();
const b = new ClassName();
```

`new` 키워드로 class를 object로 생성하는 것을 막아야 함

```tsx
class ClassName {
  private constructor() {}
}
```

→ 어디서든지 함부로 생성할 수 없도록 `private` 접근 지정자 사용

<br/>

```tsx
class ClassName {
  private static instance: ClassName | null = null;
  public static getInstance() {
    // ClassName으로부터 만든 object가 있으면 그것을 리턴
    // 없을 경우 만들어서 리턴
    if (ClassName.instance === null) {
      ClassName.instance = new ClassName(); // class 내부이므로 private 접근 가능
    }

    return ClassName.instance;
  }

  private constructor() {}
}

const a = ClassName.getInstance();
const b = ClassName.getInstance();
```

```tsx
class ClassName {
  private static instance: ClassName | null = null;
  public static getInstance(): ClassName {
    // ClassName으로부터 만든 obejct가 없으면 만든다
    if (ClassName.instance === null) {
      ClassName.instance = new ClassName();
    }

    return ClassName.instance;
  }

  private constructor() {}
}

const a = ClassName.getInstance();
const b = ClassName.getInstance();

console.log(a === b);  // true
```