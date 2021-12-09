## Slot

### Fallback Contents

- `slot` 태그 사이에서 내용이 없을 때 출력되는 것
- 컴포넌트 사용 시 기본적인 콘텐츠 삽입하게 되면 해당 `slot` 태그가 전부 대체되어 콘텐츠로 삽입되게 됨
- 콘텐츠가 없는 경우 `slot` 태그 사이에 있는 내용을 기본적으로 출력하게 됨

동작

- `App`의 `MyBtn` 안에는 내용 X, `MyBtn`에서는 `slot` 태그 사이에 Apple을 입력했을 경우 버튼의 이름 Apple로 나타남
- `MyBtn` 안에 Banana 입력할 경우에는 Apple이 아닌 Banana 출력

App.vue

```jsx
<template>
  <MyBtn>
    Banana
  </MyBtn>
</template>

<script>
import MyBtn from '~/components/MyBtn'
export default {
  components: {
    MyBtn
  }
}
</script>
```

MyBtn.vue

```jsx
<template>
  <div class="btn">
    <slot>Apple</slot>
  </div>
</template>

<style scoped>
  .btn {
    display: inline-block;
    margin: 4px;
    padding: 6px 12px;
    border-radius: 4px;
    background-color: gray;
    color: white;
    cursor: pointer;
  }
</style>
```

<br/>

#### `MyBtn` 사이에 `span` 태그 추가

- (B)Banana라는 이름의 버튼 생성
- 두 개의 `span` 태그의 순서를 바꿀 경우 문자 순서도 바뀌어 나타남

App.vue

```jsx
<template>
  <MyBtn>
    <span>(B)</span>
    <span>Banana</span>
  </MyBtn>
</template>
```

<br/>

### 순서를 정확하게 하고 싶은 경우

이름을 갖는 슬롯(Named Slot) 적용

- (B)를 아이콘, Banana를 텍스트로 인식하여 작업
- `v-slot`의 약어: `#`
- 순서를 보장했기 때문에 `#icon`을 `#text`밑으로 순서를 바꾸어도 출력 순서는 icon - text 순서

MyBtn.vue

- 정확한 위치 지정

```jsx
<template>
  <div class="btn">
    <slot name="icon"></slot>
    <slot name="text"></slot>
  </div>
</template>
```

App.vue

- `v-slot(#)`을 통하여 출력할 내용 입력

```jsx
<template>
  <MyBtn>
    <template #icon>
      <span>(B)</span>
    </template>
    <template #text>
      <span>Banana</span>
    </template>
  </MyBtn>
</template>
```