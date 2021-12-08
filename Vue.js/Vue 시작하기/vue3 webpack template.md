## Vue3 Webpack Template
[전체 코드](https://github.com/plutoin/vue3-webpack-template)

<br/>

1. 기존에 사용했던 [webpack-template-basic](https://github.com/plutoin/webpack-template-basic) 프로젝트를 vue3-webpack-template으로 사용

```bash
npx degit plutoin/webpack-template-basic vue3-webpack-template
```

<br/>

2. 생성된 프로젝트에 src 폴더 생성 후 하위에 `App.vue`와 `main.js` 생성
- 기존 `main.js` 파일과 js 폴더 삭제

<br/>

3. vue 설치
- vue만 입력할 경우 2 버전 설치됨
- 브라우저에서 동작하는 패키지 때문에 `-D` 사용하지 않고 일반 의존성으로 설치

```bash
npm i vue@next
```

<br/>

4. 추가 패키지 설치

```bash
npm i -D vue-loader@next vue-style-loader @vue/compiler-sfc
```

<br/>

5. `webpack.config.js` 파일 수정

```jsx
module.exports = {
  // 파일을 읽어들이기 시작하는 진입점 설정
  entry: './src/main.js',
	// 기존의 ./js/main.js 경로에서 src로 변경
```

`module` 안의 `rules`에서 `.vue` 확장자 파일 해석할 수 있도록 규칙 생성

- `rules`에 정규 표현식 추가
- `use`에서 `vue-style-loader`가 가장 마지막에 실행되도록 첫 번째에 삽입

```jsx
module: {
    rules: [
      {
        test: /\.vue$/,
        use: 'vue-loader'
      },
      {
        test: /\.s?css$/,
        use: [
          // 순서 중요
          'vue-style-loader',   // vue의 style 태그를 해석하고 동작시키는 webpack 로더
          'style-loader',
          'css-loader',
          'postcss-loader',
          'sass-loader'
        ]
      },
      {
        test: /\.js$/,
        use: [
          'babel-loader'
        ]
      }
    ]
  },
```

`VueLoaderPlugin`이라는 이름으로 vue-loader 내용을 가져오도록 맨 위에 작성 후 `plugin`에 생성자로 작성

```jsx
const { VueLoaderPlugin } = require('vue-loader')
```

```jsx
plugins: [
    new HtmlPlugin({
      template: './index.html'
      // 반환된 결과가 첫 번째 배열 데이터로 삽입
    }),
    new CopyPlugin ({
      patterns: [
        { from: 'static' }
        // 이미지와 파비콘이 포함된 static 폴더 지칭
      ]
    }),
    new VueLoaderPlugin()
		// 생성자 함수로 실행
  ],
```

<br/>

6. App.vue 작성
- Vue 프로젝트의 시작이 될 수 있도록

```vue
<template>
  <h1></h1>
</template>

<script>
export default {
  data () {
    return {
      message: 'Hello Vue!!!'
    }
  }
}
</script>
```

main.js

```jsx
import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount('#app')
// App.vue에서 내용을 입력해 두었으므로 App으로 가져옴
```

개발 서버 열어 확인

<img src="../images/1-4.png" width="200px" />

<br/>

import 문에서 파일 확장자 삭제

- 오류 발생

```jsx
import App from './App'
```

- 확장자 없이도 인식할 수 있도록 설정
    - webpack.config.js
        - `.js` 확장자 파일, `.vue` 확장자 파일의 확장자를 명시하지 않아도 동작
    
    ```jsx
    module.exports = {
      resolve: {
        extensions: ['.js', '.vue']
      },
    ```
    
<br/>

7. src 폴더 하위에 `HelloWorld.vue` 파일 생성
- images 폴더 src 폴더 안으로 이동한 후 assets로 폴더명 변경

```vue
<template>
  <img src="~assets/logo.png" alt="HEROPY" />
</template>
```

특정한 파일을 읽어 브라우저에 출력시키는 webpack의 로더

```bash
npm i -D file-loader
```

<br/>

webpack.config.js 파일 수정

- 경로 별칭 시 별칭이 지칭하는 실제 경로로 이동

```jsx
module.exports = {
  resolve: {
    extensions: ['.js', '.vue'],
    // 경로 별칭
    alias: {
      '~': path.resolve(__dirname, 'src'),
      'assets': path.resolve(__dirname, 'src/assets')
    }
  },
```

```jsx
{
        test: /\.js$/,
        use: [
          'babel-loader'
        ]
      },
      {
        test: /\.(png|jpe?g|gif|webp)$/,
        use: 'file-loader'
      }
    ]
  },
```

<br/>

App.vue 파일 수정

- `~` 를 src 폴더로 지정해 두었기 때문에 components 폴더 바로 찾기 가능

```vue
<template>
  <h1>{{ message }}</h1>
  <HelloWorld />
</template>

<script>
import HelloWorld from '~/components/HelloWorld'
export default {
  components: {
    HelloWorld
  },
  data () {
    return {
      message: 'Hello Vue!!!'
    }
  }
}
</script>
```

개발 서버 오픈

<img src="../images/1-5.png" width="300px" />