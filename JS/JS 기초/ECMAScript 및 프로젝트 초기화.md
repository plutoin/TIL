## ECMA스크립트

- ECMA-262 기술 규격에 따라 정의하고 있는 표준화된 스크립트 프로그래밍 언어
- 자바스크립트를 표준화하기 위해 만들어짐
- ECMAScript 2015(6버전)부터 전성기

5 버전과 6 버전의 차이
  - IE와 같은 구 버전의 브라우저는 5 버전 이하에서 지원, 신형 브라우저는 6 버전 이상에서 지원
  - [더 많은 정보](https://ko.wikipedia.org/wiki/ECMA%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8)


## 프로젝트 초기화

```bash
npm init -y
npm install parcel-bundler -D
```

package.json에 해당 내용 입력

```json
"scripts": {
    "dev": "parcel index.html",
    "build": "parcel build index.html"
  }
```

개발 서버 열기

```bash
npm run dev
```

- 터미널 휴지통 모양 클릭해서 닫을 경우 서버도 닫히므로 계속 열어 두거나 닫기 아이콘 눌러서 내려 둘 것
