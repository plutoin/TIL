## 컴포넌트 - Provide Inject

동작

- App.vue의 `data`에서 정의한 `message`라는 데이터를 Child에서 출력하기 위해 App → Parent → Child로 `props`를 이용하여 한 단계씩 내려 주고 있음

App.vue

- `msg`라는 `props` 부분에 `message`라는 데이터를 연결해서 사용함

```vue
<template>
  <Parent :msg="message" />
</template>

<script>
import Parent from '~/components/Parent'

export default {
  components: {
    Parent
  },
  data() {
    return {
      message: 'Hello World!'
    }
  }
}
</script>
```

Parent.vue

- App.vue의 `msg`를 받아 `props`를 정의하여 `template`에서 사용

```vue
<template>
  <Child :msg="msg" />
</template>

<script>
import Child from '~/components/Child'

export default {
  components: {
    Child
  },
  props: {
    msg: {
      type: String,
      default: ''
    }
  }
}
</script>
```

Child.vue

```vue
<template>
  <div>
    {{ msg }}
  </div>
</template>

<script>
export default {
  props: {
    msg: {
      type: String,
      default: ''
    }
  }
}
</script>
```

<br/>

### Provide / Inject

- `msg` 데이터를 `Child`에 전달하는 역할을 제외하고는 사용하고 있지 않지만 정의하여 데이터를 다뤄야 한다는 점을 개선시킬 수 있음

App.vue

- `provide` 옵션을 통해 `msg` 데이터를 Child로 보냄

```vue
<template>
  <button @click="message = 'Good?'">
    Click!
  </button>
  <h1>App: {{ message }}</h1>
  <Parent />
</template>

<script>
import Parent from '~/components/Parent'

export default {
  components: {
    Parent
  },
  data() {
    return {
      message: 'Hello World!'
    }
  },
  provide() {
    return {
      msg: this.message
    }
  }
}
</script>
```

Parent.vue

- `props` 삭제

```vue
<template>
  <Child />
</template>

<script>
import Child from '~/components/Child'

export default {
  components: {
    Child
  }
}
</script>
```

Child.vue

- `props` 삭제 후 `inject` 옵션 추가하여 배열 데이터로 `provide`에서 `msg`로 만들었기 때문에 `msg`로 입력
- 해당 내용이 `template`의 `msg`로 전달됨

```vue
<template>
  <div>
    Child: {{ msg }}
  </div>
</template>

<script>
export default {
  inject: ['msg']
}
</script>
```

<img src="../images/2-45.gif" width="200px" />

<br/>

### 데이터를 전달해서 출력하는 용도로 만들거나 반응성을 유지하도록 작성하고 싶은 경우

- `provide`를 통해 반응성을 유지해 주는 데이터를 만들려면 `computed` 함수를 실행하여 내부에 콜백 함수를 만듦
- 콜백 함수 내에서 특정한 반응성을 가지고 싶은 데이터를 반환

App.vue

- `computed`를 이용하여 계산된 데이터 반환 가능
- 반환된 내용이 `msg`로 들어가 동작

```vue
<template>
  <button @click="message = 'Good?'">
    Click!
  </button>
  <h1>App: {{ message }}</h1>
  <Parent />
</template>

<script>
import Parent from '~/components/Parent'
import { computed } from 'vue'

export default {
  components: {
    Parent
  },
  data() {
    return {
      message: 'Hello World!'
    }
  },
  provide() {
    return {
      msg: computed(() => this.message)
    }
  }
}
</script>
```

Child.vue

- `msg`는 `provide`에서 넘어온 계산된 객체 데이터이므로 정확히 내가 원하는 데이터를 출력하고자 한다면 `value` 속성 사용

```vue
<template>
  <div>
    Child: {{ msg.value }}
  </div>
</template>

<script>
export default {
  inject: ['msg']
}
</script>
```

<img src="../images/2-46.gif" width="200px" />

<br/>

### 요약

- App은 Child의 상위, 혹은 조상 컴포넌트라고 부를 수 있음
- 조상 컴포넌트에서 자식 컴포넌트로 데이터를 내려 줄 때는 `props` 개념 사용, 자식이 자식 컴포넌트로 내려 줄 때도 `props` 사용
- 조상 컴포넌트에서 자식을 거치지 않고 후손 컴포넌트로 바로 데이터를 내려 줄 때는 Parents처럼 매개체 역할을 해 주는 컴포넌트가 필요함
    - 과정을 최대한 생략하기 위해 `provide`를 이용하여 데이터 정의, 중간 매개체 과정 없이 Child로 빠르게 데이터 전송 가능
    - 전달되는 데이터는 `props`와는 다르게 반응성을 가지지 않아 조상 컴포넌트에서 데이터가 변경되더라도 하위 요소에서는 화면 갱신 구조 X
        - `computed`라는 계산된 데이터를 가지고 와 반응성을 유지한 상태로 조상 → 후손으로 데이터 연결 구조 생성