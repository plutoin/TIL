## module

css 폴더 생성 후 하위에 `main.css` 파일 추가

```css
body {
  background-color: orange;
}
```

`main.js`에 css 가져오기

```jsx
import './css/main.css'

console.log('webpack!')
```

- webpack의 진입점이 `main.js`이므로 제일 먼저 `main.js`를 읽기 시작
- 연결되어져 있는 css가 webpack이 읽어 와 `index.html`과 병합하여 `dist`로 반환
- webpack은 css 파일을 읽지 못하고 어떤 파일과 합친 후 `dist`로 내어 주는 것만 할 수 있음

<br/>

css 파일을 읽을 수 있는 패키지 설치

```bash
npm i -D css-loader style-loader
```

<br/>

`webpack.config.js` 파일 코드 추가

- `test`: `.css` 확장자를 가지는 파일을 찾는 정규 표현식 작성
- `use`
    - `css-loader`: js에서 css 파일을 해석할 수 있도록 함
    - `style-loader`: css-loader에서 해석된 내용을 index.html에 삽입
    - `style-loader`, `css-loader` 순으로 작성해야 함

```jsx
/* output과 plugin 사이에 추가*/
module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          'style-loader',
          'css-loader'
        ]
      }
    ]
  },
```

<br/>

개발 서버 오픈 후 결과

<img src="../images/2-5.png" width="300px" />

<br/>

색상 바꿔서 동작시켜도 잘 동작함

<img src="../images/2-6.png" width="300px" />
