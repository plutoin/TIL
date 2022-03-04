## Cypress API
### 1. click

- 버튼을 클릭할 수 있게 하는 메소드

```jsx
cy.get('.btn').click() // Click on button
cy.focused().click() // Click on el with focus
cy.contains('Welcome').click() // Click on first el containing 'Welcome'
```

### 2. contains

- 특정 텍스트가 포함되어 있는 DOM 요소 확인 용도
- `nav` 클래스를 가진 요소가 About이라는 텍스트를 가지고 있는지 확인 가능

```jsx
cy.get('.nav').contains('About') // Yield el in .nav containing 'About'
cy.contains('Hello') // Yield first el in document containing 'Hello'
```

### 3. get

- 선택자를 통해 DOM 요소를 확인 가능
- `list` 요소의 자식 요소인 `li` 요소 확인 가능

```jsx
cy.get('.list > li') // Yield the <li>'s in .list
```

### 4. select

- `select`가 가지고 있는 옵션을 선택하는 메소드

```jsx
cy.get('select').select('user-1') // Select the 'user-1' option
```

### 5. url

- 현재 활성화된 페이지의 url 정보를 얻을 수 있음

```jsx
cy.get('select').select('user-1') // Select the 'user-1' option
```

- `should` 메소드를 통해 기댓값을 매칭 가능
- users/1/edit 부분이 주소에 포함(include)되어 있는지 확인 가능
- `eq`(equal)을 통해 url과 일치하는지 확인 가능

```jsx
// clicking the anchor causes the browser to follow the link
cy.get('#user-edit a').click()
cy.url().should('include', '/users/1/edit') // => true
cy.url().should('eq', 'http://localhost:8000/users/1/edit') // => true
```

### 6. should

- 단위 테스트에서 `expect를` 통해 테스트 코드를 작성하듯이 `should도` 유사한 기능
    - `expect` 함수로 어떤 값을 제공해 기댓값과 일치하는지 확인
    - 제공받은 값이 기댓값으로 일치할 것이라는 것을 단언한다는 뜻
- 특정한 요소를 찾거나 동작시키는 개념보다는 검증해 내는 개념
- `error` 클래스를 가지고 있는 요소를 찾아 `be.empty`, 즉 비어 있을 것을 기대
- Login이라는 텍스트를 가진 요소를 찾아 `be.visible`, 즉 화면에 보여지고 있는지 확인

```jsx
cy.get('.error').should('be.empty') // Assert that '.error' is empty
cy.contains('Login').should('be.visible') // Assert that el is visible
cy.wrap({ foo: 'bar' }).its('foo').should('eq', 'bar') // Assert the 'foo' property equals 'bar'
```