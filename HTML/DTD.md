## DTD

```html
<!DOCTYPE html>
```

- DOCTYPE(DTD, Document Type Definition)
- 문서의 HTML 버전 지정
- 마크업 언어에서 문서 형식 정의
- 웹 브라우저가 어떤 HTML 버전의 해석 방식으로 페이지를 이해하면 되는지를 알려 줌
- HTML5가 가장 최신이자 표준 버전

```html
<!DOCTYPE html PUBLIC ~(생략)>
```

XTML 버전

```html
<html>
	<head>
	</head>
	<body>
	</body>
</html>
```

`<html>~</html>`

- 문서의 전체 범위

`<head>~</head>`

- 문서의 정보를 나타내는 범위 
- css 파일 link 태그 사용
- js 파일 script src로 사용
   `console.log('문자열');`  
   입력한 내용 확인하기: 개발자 도구 콘솔창 확인  
- 웹 브라우저가 해석해야 함  
- 웹 페이지의 제목, 설명, 사용할 파일 위치, 스타일 같은 웹 페이지의 보이지 않는 정보 작성  
- css 파일에다 작성할 수 있는 스타일시트 내용 작성 `<style>` 태그 사용

`<body>~</body>`

- 문서의 구조를 나타내는 범위
- 사용자 화면을 통해 보여지는 로고, 헤더, 푸터, 내비게이션 메뉴, 버튼, 이미지 같은 웹 페이지의 보여지는 구조 작성 범위

```html
<link rel="stylesheet" href="main.css">
<link rel="icon" href="./favicon.png">
rel 가져올 문서와의 관계
href 가져올 문서의 경로
```

```html
<script src="main.js"></script> <!-- JS 파일 가져오는 경우 -->
<script>
  console.log('Hello World!') /* JS를 HTML 문서 안에 작성하는 경우 */
</script>
```

```html
<meta charset="UTF-8"> <!-- 문자 인코딩 방식 -->
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
- HTML 문서의 제작자, 내용, 키워드 같은 여러 정보를 검색 엔진이나 브라우저에 제공  
- viewport는 모바일을 위한 것 웹은 해당 없음

#### alt(Alternate)
```html
<img src="logo.png" alt="">
```
- 이미지가 출력되지 못하는 경우 대신 출력할 텍스트 = 대체 텍스트
- 이미지 경로가 잘못되거나 네트워크가 불안정한 경우 등 이미지를 출력할 수 없는 다양한 상황에 이미지 대신 화면에 나올 글자

<br/>

상대 경로: ./(주변 파일 탐색) ../(상위 폴더로)

절대 경로: http(https) /(최상위 경로)

```html
<img src="/images/logo.png" alt="">
<!-- images 앞에 localhost:5500 생략된 절대 경로 -->
```