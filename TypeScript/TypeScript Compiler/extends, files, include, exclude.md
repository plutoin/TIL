## extends
- 파일(상대) 경로명: `string`
- TypeScript 2.1 new Spec

```tsx
{
  ...,
  "extendsDefinition": {
    "properties": {
      "extends": {
        "description": "Path to base configuration file to inherit from. Requires TypeScript version 2.1 or later.",
        "type": "string"
      }
    }
  },
  ...,
}
```

ex)

```tsx
{
	"extends": "/base.json",
	"compilerOptions": {
	}
}
```

base.json

```tsx
{
	"compilOptions": {
		"strict": true
	}
}
```

→ json 파일에서 지정해 줌으로써 `tsconfig` 파일에서 `strict`를 건드릴 필요가 없음

<br/>

## files, include, exclude

셋 다 설정이 없을 경우 전부 컴파일

### files

- 상대 혹은 절대 경로의 리스트 배열
- `exclude`보다 강함

### include, exclude

- `glob` 패턴(.gitignore와 유사)
- **include**
    - `exclude`보다 약함
    - 같은 걸 사용하면 .ts / .tsx / .d.ts 만 include (allowJS)
- **exclude**
    - 설정 안하면 4가지(node_modules, bower_components, jspm_packages, `<outDir>`)를 `default` 로 제외
    - `<outDir>` 은 `include`에 있어도 항상 제외