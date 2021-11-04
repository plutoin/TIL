## entry / output
[webpack](https://webpack.js.org/configuration/entry-context/)의 홈페이지에서 다양한 내용 확인 가능

- `entry`: 진입점을 하나뿐만 아닌 여러개 지정 가능
- `output.path`: 결과물이 반환될 디렉토리를 절대경로로 명시해야 함
    - `__dirname`: 해당하는 파일의 실제 경로를 나타내는 `node.js`의 전역변수

```jsx
const path = require('path');

module.exports = {
  //...
  output: {
    path: path.resolve(__dirname, 'dist/assets'),
  },
};
```

- `clean` 옵션

```jsx
module.exports = {
  //...
  output: {
    clean: true, // Clean the output directory before emit.
  },
};
```
<br/>

`main.js` 파일 생성

```bash
console.log('webpack!')
```

`webpack.config.js` 파일 수정

```jsx
// import
const path = require('path')
// node.js에서 언제든지 사용할 수 있는 모듈

// export
module.exports = {
  // 파일을 읽어들이기 시작하는 진입점 설정
	entry: './js/main.js',

  // 결과물(번들)을 변환하는 설정
  output: {
    path: path.resolve(__dirname, 'dist'), 
    // webpack이라는 bundler를 동작시키면 어떤 경로에다가 어떤 결과물을 내어 줄 것인가
    // resolve는 인수들의 경로를 합쳐 주는 역할
    // __dirname은 node.js의 전역변수
		// 둘의 경로를 합친 절대 경로를 output의 path로 전달
    filename: 'main.js'
  }
}
```

→ `dist`라는 폴더에 `main.js`라는 파일 이름으로 entry에서 사용한 진입점의 `main.js`의 모든 내용을 번들로 만들어 합친 후 내어 줌

<br/>

결과 확인

```bash
npm run build
```

→ dist 폴더 생성, 하위에 `main.js` 파일 생성

→ 진입점의 `main.js` 파일 내용과 동일

<br/>

`webpack.config.js` 파일 일부 수정

```jsx
output: {
	path: path.resolve(__dirname, 'public'), 
  filename: 'app.js'
}
```

→ 결과: public 폴더 생성 후 하위에 `app.js` 파일 생성

→ `app.js` 파일 내용 진입점의 `main.js`의 파일 내용과 동일

<br/>

`clean` 옵션 사용 후 빌드 하면 기존 파일 삭제 가능

```jsx
output: {
    path: path.resolve(__dirname, 'public'), 
    filename: 'main.js',
    clean: true
  }
```

→ 위에서 생성된 `app.js` 파일이 지워지고 `main.js`가 생성

<br/>

`output`에서 `path` 경로를 `dist`로 지정하지 않아도 기본값은 `dist`

```jsx
output: {
    // path: path.resolve(__dirname, 'dist'), 
    // filename: 'main.js',
    clean: true
  }
```

→ 주석 해제했을 때와 동일한 결과 나옴

→ `dist` 폴더 생성, 하위에 `main.js` 파일 생성