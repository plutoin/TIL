## npm 개요

NPM(Node Package Manager)
- 전 세계의 개발자들이 만든 다양한 기능(패키지, 모듈)들을 관리

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1ba4c623-17fd-49c2-b804-632e580540eb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T182412Z&X-Amz-Expires=86400&X-Amz-Signature=1229cd119ec633f08ccb70bac73c85ebe618d24d05433ffda195f65d6f87d471&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="500px" />

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/42b7899f-d475-4d3e-bbcf-351f9236cc41/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T182454Z&X-Amz-Expires=86400&X-Amz-Signature=cd7faa4680ffad27875e5dcf0cd1b183cb1ff7ed46d0b9af59a7dc0c685829da&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="500px" />

- npm으로 패키지 관리

```bash
npm init -y
```

- package.json 파일 생성됨

```json
{
  "name": "test",
  "version": "1.0.0",
  "description": "",
	"main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

- 패키지에 필요한 파일 설치

```bash
npm install parcel-bundler -D
```

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8f06f6d1-77a7-41e2-941c-eb81887ceb9b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T182517Z&X-Amz-Expires=86400&X-Amz-Signature=3a9f4f97b30c7ce117948b3eb34cd4b3f3403a38824de6d0c5b4bb9bbdab4614&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="400px" />

devDependencies 밑에 설치된 parcel-bundler 표시됨

- lodash 패키지 설치

```bash
npm install lodash
```

- node_modules 패키지 지워졌을 때 설치

```bash
npm install
npm i
```

package-lock.json 파일은 자동으로 관리되는 파일

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a1b3547d-fd77-4fce-a0dd-69aa3dfd943a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T182550Z&X-Amz-Expires=86400&X-Amz-Signature=1abec9b0baf47e2e6dd4a08d66eebbe70e1820cc7922f32e83d7796321d1a64f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="500px" />

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ffa8830b-38ae-4330-a5f6-ff38c1342d3a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T182605Z&X-Amz-Expires=86400&X-Amz-Signature=696fa7d4490524899306a642c8ef9d6a7e045a6d28162020a328ded68e92a112&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="500px" />

개발용 의존성 패키지: 개발할 때는 필요하지만 웹 브라우저에서는 동작 X
일반 의존성: 웹 브라우저에서 사용되기도 함


## npm 프로젝트의 버전 관리(.gitignore)

node_modules, dist, .cache 폴더는 각각 `npm i` `npm run build` 를 통해 필요할 때마다 생성할 수 있으므로 버전 관리 할 필요가 없음 오히려 버전 관리 시 비효율적이게 됨

버전 관리에 제외하기 위해 `.gitignore` 파일 생성 후 다음과 같이 입력

```bash
.cache/
dist/
node_modules/
```