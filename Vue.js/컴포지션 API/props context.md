## props / context

App.vue

```vue
<template>
  <MyBtn
    class="heropy"
    style="color: red"
    color="#ff0000"
    @hello="log">
    Apple
  </MyBtn>
</template>

<script>
import MyBtn from '~/components/MyBtn'

export default {
  components: {
    MyBtn
  },
  methods: {
    log() {
      console.log('Hello World!')
    }
  }
}
</script>
```

MyBtn.vue

- `emits`를 이용하여 `hello` 이벤트 연결
    - App.vue의 `@hello="log"`
    - `hello` 메소드 내부에서 `emit` 통해 연결

```vue
<template>
  <div
    v-bind="$attrs"
    class="btn"
    @click="hello">
    <slot></slot>
  </div>
</template>

<script>
export default {
  inheritAttrs: false,
  props: {
    color: {
      type: String,
      default: 'gray'
    }
  },
  emits: ['hello'],
  mounted() {
    console.log(this.color)
    console.log(this.$attrs)
  },
  methods: {
    hello() {
      
    }
  }
}
</script>
```

<br/>

### 컴포지션 API

- `setup` 내부에서는 `this`를 사용할 수 없기 때문에 `props`와 `context` 활용
    - props.color
    - context.attrs ($ 사인 제거)
- `mounted` 라이프 사이클 사용 위해 객체 구조 분해로 vue 패키지에서 `onMounted` 가지고 옴

```vue
<template>
  <div
    v-bind="$attrs"
    class="btn"
    @click="hello">
    <slot></slot>
  </div>
</template>

<script>
import { onMounted } from 'vue'
export default {
  inheritAttrs: false,
  props: {
    color: {
      type: String,
      default: 'gray'
    }
  },
  emits: ['hello'],
  setup(props, context) {
    function hello() {
      context.$emit('hello')
    }
    onMounted(() => {
      console.log(props.color)
      console.log(context.attrs)
    })

    return {
      hello
    }
  }
}
</script>
```

<br/>

### 정리

- 기존의 방법에서는 `this`를 활용하여 `color` 접근, `$` 사인을 이용하여 상속받은 모든 속성의 객체를 활용하여 사용할 수도 있음
    - `setup`에서는 사용할 수 없기 때문에 `props`와 `context`를 순서대로 제공
    - `props`에서는 실제 데이터를, `context`에서는 `$` 사인을 사용하지 않는 `attrs`라는 상속받은 모든 속성을 가지고 있는 객체 활용