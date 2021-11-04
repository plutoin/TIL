## SCSS

`main.css`와 상위 폴더인 css를 scss 확장자와 폴더명으로 변경

`main.js`의 import문의 css 파일 확장자를 scss로 변경

`webpack.config.js` 파일의 module 옵션 변경

```jsx
module: {
    rules: [
      {
        test: /\.s?css$/,
				// scss와 css 확장자 파일 모두 찾도록 작성
        use: [
          'style-loader',
          'css-loader'
        ]
      }
    ]
  },
```

<br/>

scss를 가져올 수 있도록 추가적인 loader 패키지 설치

- `sass-loader`: webpack에서 scss 파일을 읽을 수 있도록 함
- `sass`: 문법을 해석할 수 있도록 하는 모듈

```bash
npm i -D sass-loader sass
```

<br/>

`sass-loader`가 `css-loader`보다 먼저 실행되도록 작성

```jsx
module: {
    rules: [
      {
        test: /\.s?css$/,
        use: [
          'style-loader',
          'css-loader',
          'sass-loader'
        ]
      }
    ]
  },
```

<br/>

`main.scss` 파일 수정

```jsx
$color--black: #000;
$color--white: #fff;

body {
  background-color: $color--black;
  h1 {
    color: $color--white;
    font-size: 40px;
  }
}
```

<br/>

개발 서버 오픈 후 결과

<img src="../images/2-7.png" width="300px" />