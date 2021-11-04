## npx / degit

`degit`: github의 특정 원격 저장소를 현재 경로로 다운

- `degit`을 사용하려면 별도로 설치해야 하나 npx로 그냥 사용 가능
- `npx`: `node.js`에서 사용할 수 있는 명령

```bash
npx degit plutoin/webpack-template-basic webpack-template-test
```

→ plutoin/webpack-template-basic 저장소의 내용을 webpack-template-test라는 폴더 이름으로 현재 경로에 다운하겠다는 듯

→ ls로 생성 확인 가능

<br/>

`npx degit`은 버전 관리 된 내용까지 가져오지 않지만 `git clone`은 버전 관리 내용까지 전부 가지고 옴

- 템플릿으로 이용, 즉 현재 프로젝트를 이용해 새로운 프로젝트를 만들고자 하는 경우는 `git clone`이 적합하지 않고 `npx degit` 사용