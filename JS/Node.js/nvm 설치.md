## nvm 설치

homebrew 설치
- [Homebrew](https://brew.sh/index_ko)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

nvm 설치

```bash
brew install nvm
```

> m1 사용 시 `brew install nvm`이 실행되지 않고 `zsh: command not found: nvm` 문구가 뜨게 됨

해결방법
- nvm이 사용할 디렉토리 생성 후 vi 편집기 통해 ~/.zshrc로 진입

```bash
mkdir ~/.nvm
vi ~/.zshrc
```

편집기에 해당 내용 붙여넣기 후 `:wq`로 저장 후 빠져나오기

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "/usr/local/opt/nvm/nvm.sh" ] && . "/usr/local/opt/nvm/nvm.sh"  # This loads nvm
[ -s "/usr/local/opt/nvm/etc/bash_completion.d/nvm" ] && . "/usr/local/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion
```

```bash
nvm ls
```

아래의 내용 나오면 성공  
<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/000cebe2-ed0b-424e-9863-7894a8b20aed/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210730%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210730T182249Z&X-Amz-Expires=86400&X-Amz-Signature=0957b4ae5aaf26bb203ab3cff2f3cf84353f74902c4b7b9ae43dc706512d0bfd&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22" width="300px" />


- node.js 설치

설치 후 `node —version` `node` `-v node`로 확인 가능
(되도록이면 10버전 이상을 설치할 것)

`nvm ls`로 버전 목록 확인 가능

```bash
nvm install 설치하고자 하는 node 버전
node --version
nvm ls
```

- node.js 삭제하기

여러 버전 설치한 경우 설치하고자 하는 버전만 골라서 삭제 가능

```bash
nvm uninstall 삭제하고자 하는 버전
```