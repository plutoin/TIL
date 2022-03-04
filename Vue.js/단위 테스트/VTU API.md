## VTU API

- [Docs](https://test-utils.vuejs.org/api/#attrs)

### 1. attrs

- `mount`에서 반환된 `wrapper` 객체를 반환하여 메소드로 `attributes` 메소드 실행
- 메소드에서 반환 후 해당 컴포넌트에 연결되어 HTML 속성들을 객체 형식으로 반환하여 테스트 형식으로 확인 가능

```jsx
import { mount } from '@vue/test-utils'
import Component from './Component.vue'

test('attrs', () => {
  const wrapper = mount(Component, {
    attrs: {
      id: 'hello',
      disabled: true
    }
  })

  expect(wrapper.attributes()).toEqual({
    disabled: 'true',
    id: 'hello'
  })
})
```

### 2. data

- `mount`를 함수처럼 사용해 첫 번째 인수를 컴포넌트, 두 번째 인수는 옵션으로 작성
- 옵션에는 `data`를 실제 컴포넌트 연결할 때처럼 메소드 형식으로 작성하여 데이터를 `return` 키워드로 반환하듯이 작성
    - `message`가 world라는 내용으로 바뀌도록 작성
- html에 Hello World라는 문자 데이터가 있는지 테스트로 확인

```vue
<template>
  <div>Hello {{ message }}</div>
</template>

<script>
export default {
  data() {
    return {
      message: 'everyone'
    }
  }
}
</script>
```

```jsx
import { mount } from '@vue/test-utils'
import Component from './Component.vue'

test('data', () => {
  const wrapper = mount(Component, {
    data() {
      return {
        message: 'world'
      }
    }
  })

  expect(wrapper.html()).toContain('Hello world')
})
```

### 3. props

- 테스트 코드 내부에서 `mount`를 함수처럼 사용
- 두 번째 인수인 옵션에서 `count`를 5로 할당
- `Count: {{ count }}` 형식으로 출력하기 때문에 Count: 5의 형태로 출력됨
    - 이 결과가 맞는지 테스트로 확인하는 예제

```vue
<template>
  <span>Count: {{ count }}</span>
</template>

<script>
export default {
  props: {
    count: {
      type: Number,
      required: true
    }
  }
}
</script>
```

```jsx
import { mount } from '@vue/test-utils'
import Component from './Component.vue'

test('props', () => {
  const wrapper = mount(Component, {
    props: {
      count: 5
    }
  })

  expect(wrapper.html()).toContain('Count: 5')
})
```

### 4. global

- global.plugins
- 나만의 플러그인을 만들어 `myPlugin`의 이름으로 가지고 올 수 있음
- mount의 두 번째 옵션으로 global 옵션 지정, `plugin`에 배열 데이터 형식의 `myPlugin`을 할당
    - store, router, loadImage 등의 플러그인을 `global` 하위의 `plugins`에 등록 가능

```jsx
import { mount } from '@vue/test-utils'
import Component from './Component.vue'

import myPlugin from '@/plugins/myPlugin'

test('global.plugins', () => {
  mount(Component, {
    global: {
      plugins: [myPlugin]
    }
  })
})
```

### 5. attributes

- wrapper 객체를 통해 id 값을 추출 및 foo라는 문자 데이터를 가지고 있는지 확인
- wrapper 객체를 통해 class 값을 추출 및 bar라는 문자 데이터를 가지고 있는지 확인

```jsx
import { mount } from '@vue/test-utils'
import Component from './Component.vue'

test('attributes', () => {
  const wrapper = mount(Component)

  expect(wrapper.attributes('id')).toBe('foo')
  expect(wrapper.attributes('class')).toBe('bar')
})
```

```vue
<template>
  <div id="foo" :class="className" />
</template>

<script>
export default {
  data() {
    return {
      className: 'bar'
    }
  }
}
</script>
```

### 6. exists

- `wrapper` 객체 통해 `find` 메소드로 `span` 태그가 존재(`exists`)하는지 확인 후 기댓값과 비교 테스트

```jsx
import { mount } from '@vue/test-utils'
import Component from './Component.vue'

test('exists', () => {
  const wrapper = mount(Component)

  expect(wrapper.find('span').exists()).toBe(true)
  expect(wrapper.find('p').exists()).toBe(false)
})
```

### 7. find

- 각각의 코드에서 span, p 태그를 찾음
- 메소드 체이닝으로 exists를 사용한다면 존재하는지 아닌지 여부까지 확인 가능

```vue
<template>
  <span>Span</span>
  <span data-test="span">Span</span>
  <span ref="span">Span</span>
</template>
```

```jsx
import { mount } from '@vue/test-utils'
import Component from './Component.vue'

test('find', () => {
  const wrapper = mount(Component)

  wrapper.find('span') //=> found; returns DOMWrapper
  wrapper.find('[data-test="span"]') //=> found; returns DOMWrapper
  wrapper.find({ ref: 'span' }) //=> found; returns DOMWrapper
  wrapper.find('p') //=> nothing found; returns ErrorWrapper
})
```

### 8. setData

- wrapper 객체에서 html을 확인해 Count: 0이 포함되어 있는지 확인
- wrapper 객체에서 setData 메소드를 통해 count를 1로 할당
    - 반응성을 가질 수 있을 때까지 기다려야 하므로 await 키워드 사용, 해당 함수 앞에 async 작성
- html에서 Count: 1이 포함되어 있는지 확인

```vue
<template>
  <div>Count: {{ count }}</div>
</template>

<script>
export default {
  data() {
    return {
      count: 0
    }
  }
}
</script>
```

```jsx
import { mount } from '@vue/test-utils'
import Component from './Component.vue'

test('setData', async () => {
  const wrapper = mount(Component)
  expect(wrapper.html()).toContain('Count: 0')

  await wrapper.setData({ count: 1 })

  expect(wrapper.html()).toContain('Count: 1')
})
```

### 9. unmount

- 연결된 컴포넌트를 강제적으로 연결 해제 가능
- 연결 해제 후 `unmounted` 라이프 사이클이 동작하며 unmounted!라는 문구 출력

```vue
<script>
export default {
  unmounted() {
    console.log('unmounted!')
  }
}
</script>
```

```jsx
import { mount } from '@vue/test-utils'
import Component from './Component.vue'

test('unmount', () => {
  const wrapper = mount(Component)

  wrapper.unmount()
  // Component is removed from DOM.
  // console.log has been called with 'unmounted!'
})
```

### 10. vm

- Vue Model의 약어
- Vue.js에 컴포넌트가 연결되면 사용할 수 있는 this와 같은 기능

### 11. shallowMount

- `mount`와 컴포넌트를 연결한다는 점에서는 비슷하다고 할 수 있음
- `mount` 기능 뿐만 아니라 `shallowMount`로도 컴포넌트를 테스트 환경에서 연결해 사용 가능