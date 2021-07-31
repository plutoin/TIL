## 마크다운

- 장점
  - 문법이 쉽고 간결하다
  - 관리가 쉽다
  - 지원 가능한 플랫폼과 프로그램이 다양하다
- 단점
  - 표준이 없다
  - 모든 HTML 마크업을 대신하지 못한다


## 제목, 문장, 줄바꿈

#### 1. 제목  
#~######로 제목 크기 및 중요도 조절 가능

```markdown
# 제목(Header)

# 제목 1
## 제목 2
### 제목 3
#### 제목 4
##### 제목 5
###### 제목 6
```

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0199ac3e-912c-4c3e-b4fa-302682b25c07/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T174059Z&X-Amz-Expires=86400&X-Amz-Signature=f560a325e08b64d8da425096a65596ae24735d2333dfbb373287c9c5dcd955a3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="300px" >

#### 2. 문장, 줄바꿈  
엔터가 아닌 띄어쓰기 두 번 또는 `<br />`으로 줄 바꿈

```markdown
# 문장(Paragraph)
동해물과 백두산이 마르고 닳도록
하느님이 보우하사 우리나라 만세

# 줄바꿈(Line Breaks)

동해물과 백두산이 마르고 닳도록  
하느님이 보우하사 우리나라 만세  
무궁화 삼천리 화려 강산  
대한 사람 대한으로 길이 보전하세
```

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f3f62606-bc37-43a6-bee1-b040faa4167b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T174740Z&X-Amz-Expires=86400&X-Amz-Signature=1e9b8e3b6157a293defbd8286e1af990b36e8c77f129dfdd369b3479f94a89c6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="300px" >


## 강조, 목록

#### 1. 강조  
밑줄 태그는 권장하지 않음

```markdown
# 강조(Emphasis)
_이텔릭_  
두껍게  
**_이텔릭 + 두껍게_**  
~~취소선~~  
<u>밑줄</u>
```

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0cb3b9eb-3a3d-48fd-978c-d042b62f1173/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T174758Z&X-Amz-Expires=86400&X-Amz-Signature=61e4e6dc064cd1f4d170696023bf98fb716ce51a74806c18d5c90d26b8b731ca&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="300px" >

#### 2. 목록  
`<ol>`태그와 비슷한 기능

```markdown
# 목록(List)

1. 순서가 필요한 목록
1. 순서가 필요한 목록
1. 순서가 필요한 목록
    <!-- 들여쓰기 두 번으로 하위 목록 생성 -->
    1. 순서가 필요한 목록
    1. 순서가 필요한 목록
1. 순서가 필요한 목록

- 순서가 필요하지 않은 목록
- 순서가 필요하지 않은 목록
- 순서가 필요하지 않은 목록
    <!-- 들여쓰기 두 번으로 하위 목록 생성 -->
    - 순서가 필요하지 않은 목록
    - 순서가 필요하지 않은 목록
- 순서가 필요하지 않은 목록
```

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8860eef2-abab-450d-ba06-c183ca32c6d5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T174850Z&X-Amz-Expires=86400&X-Amz-Signature=1123321c2cc1c6eb79b191ee0feddf5c24cc2698896a67d09914a3ecd1a39c3e&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="300px" >


## 링크, 이미지

#### 1. 링크

```markdown
# 링크(Links)

<a href="https://google.com">GOOGLE</a>

[GOOGLE](https://google.com)

<a href="https://naver.com" title="NAVER로 이동!">NAVER</a>
<!-- title에 내용 입력하면 커서 올렸을 때 해당 내용 표시-->

[NAVER](https://naver.com "NAVER로 이동!")

<a href="https://naver.com" title="NAVER로 이동!" target="_blank">NAVER</a>  
<!-- _blank 새 탭에 화면 띄우기, 마크다운에서 target을 제공하고 있지는 않음 -->
```

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a37e0ac7-7a9f-4c4b-9e8e-68b6af75ce0d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T174914Z&X-Amz-Expires=86400&X-Amz-Signature=950463b07a752c26ef3b3cb5e6b48167ddc6edc3d7751f0f69af5d22d1483c5c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="300px" >

2. 이미지

```markdown
# 이미지(Images)

<!-- 이미지 주소 복사해 이미지만 출력 -->
![HEROPY](https://heropy.blog/css/images/logo.png)

<!-- 이미지 클릭 시 특정 링크로 이동될 수 있도록 -->
[![HEROPY](https://heropy.blog/css/images/logo.png)](https://heropy.blog)이미지만 출력
```

> 이미지만 출력

<img src="https://heropy.blog/css/images/logo.png" width="200px" >

> 클릭 시 특정 링크로 이동

<a href="https://heropy.blog"><img src="https://heropy.blog/css/images/logo.png" width="200px"></a>


## 인용문, 코드 강조

#### 1. 인용문

```markdown
# 인라인(inline) 코드 강조

CSS에서 `background` 혹은 `background-image` 속성으로 요소에 배경 이미지를 삽입할 수 있습니다.
```

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/75b51cf1-64a7-45ae-913e-73d2e2a4c47c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T175000Z&X-Amz-Expires=86400&X-Amz-Signature=ab7166740815b7270fd2ad429a48cdcb31a55bcc27ebfec517519b3b29c184b3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="300px" >

#### 2. 코드 강조

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/54f50e60-d400-4a59-91e0-58b5b6c7c69b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T175655Z&X-Amz-Expires=86400&X-Amz-Signature=9b7ae6945e5f97d73573d6dde3b700999a968e3755230f559c56d10a34eb08a2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="300px" >

```markdown
# 블록(block) 코드 강조
```

```html
<a href="https://www.google.co.kr/" target="_blank">GOOGLE</a>
```

```css
.list > li {
  position: absolute;
  top: 40px;
}
```

```javascript
function func() {
  var a = 'AAA';
  return a;
}
```

```bash
$ git commit -m 'Study Markdown'
```

```plaintext
동해물과 백두산이 마르고 닳도록  
하느님이 보우하사 우리나라 만세
```



## 표

- 기본적으로 왼쪽 정렬
- 가운데정렬(:—:) 가운데정렬(—:) 콜론 위치로 설정 가능

```markdown
# 표(Table)

position 속성

값 | 의미 | 기본값
--|:--:|--:
static | 기준 없음 | O
relative | 요소 자신 | X
absolute | 위치 상 부모 요소 | X
fixed | 뷰포트 | X
```

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5be8f3c6-c09a-471a-ba89-efda5cc24db6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T175414Z&X-Amz-Expires=86400&X-Amz-Signature=2ee0c870e3e089d3d73583d47f5468a193551743740b313c2ebd6c1a4ea4bb48&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="300px" >


## 원시 HTML, 수평선

#### 1. 원시 HTML  
`<u></u>` 태그보다 `<span style="text-decoration: underline;>`을 더 권장

```markdown
# 원시 HTML(Raw HTML)

동해물과 <span style="text-decoration: underline;">백두산이</span> 마르고 닳도록<br />
하느님이 보우하사 우리나라 만세
```

#### 2. 수평선

```markdown
# 수평선(Horizontal Rule)

---

***

___
```

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/569988a9-140d-4cb2-86b9-a170daa6756b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T175501Z&X-Amz-Expires=86400&X-Amz-Signature=55532ae2ddfd012cf7d4ff788c34c8fadfdff3ca33e54ae9dadc985d7169db00&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="300px" >
