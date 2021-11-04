## babel

babel 패키지 설치

```bash
npm i -D @babel/core @babel/preset-env @babel/plugin-transform-runtime
```

<br/>

`.babelrc.js` 파일 생성

- `preset`: 하나씩 명시해야 하는 JS 기능을 한 번에 지원해 주는 패키지
- `plugins`: 비동기 처리를 위함

```jsx
module.exports = {
  presets: ['@babel/preset-env'],
  plugins: [
    ['@babel/plugin-transform-runtime']
  ]
}
```

<br/>

`webpack.config.js` 파일 코드 추가

- babel을 webpack이 해석하려면 `babel-loader`가 필요함

```jsx
module: {
    rules: [
      {
        test: /\.s?css$/,
        use: [
          'style-loader',
          'css-loader',
          'postcss-loader',
          'sass-loader'
        ]
      },

			// 추가
      {
        test: /\.js$/,
        use: [
          'babel-loader'
        ]
      }
    ]
  },
```

<br/>

`babel-loader` 추가 설치

```bash
npm i -D babel-loader
```