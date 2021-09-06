## Structural Type System vs Nominal Type System

### structural type system

- 구조가 같으면 같은 타입이다

```tsx
interface IPerson {
  name: string;
  age: number;
  speak(): string;
}

type PersonType = {
  name: string;
  age: number;
  speak(): string;
}

let personInterface: IPerson = {} as any;
let personType: PersonType = {} as any;

personInterface = personType;
personType = personInterface;
```

→ 타입을 명시적으로 지정할 필요 없이 구조만 같으면 되므로 일일히 타입 설정할 필요가 없음

### nominal type system

- 구조가 같아도 이름이 다르면 다른 타입

```tsx
type PersonID = string & { readonly brand: unique symbol };

function PersonID(id: string): PersonID {
  return id as PersonID;
}

function getPersonById(id: PersonID) {}

getPersonById(PersonID('id-aaaaaa'));
getPersonById('id-aaaaaa')
// error TS2345: Argument of type 'string' is not assignable to parameter of type 'PersonID'.
// Type 'string' is not assignable to type '{ readonly brand: unique symbol }'.
```

→ PersonID의 형식으로만 사용, 일반적인 문자열은 삽입 불가능

### duck typing

- 만약 어떤 새가 오리처럼 걷고 헤엄치고 꽥꽥거리는 소리를 낸다면 나는 그 새를 오리라고 부를 것이다.
- 예시는 Python, 타입스크립트는 사용하지 않음

```python
class Duck:
	def sound(self):
		print u"꽥꽥"

class Dog:
	def sound(self):
		print u"멍멍"

def get_sound(animal):
	animal.sound()

def main():
	bird = Duck();
	dog = Dog();
	get_sound(bird)
	get_sound(dog)
```