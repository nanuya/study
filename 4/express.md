# Express

> Express 는 백엔드 서버를 구축할 수 있는 API를 제공하는 유연한 웹 애플리케이션 프레임워크이다.

## 설정하기

```
$ mkdir express-demo-app
$ touch .gitignore
$ echo "/node_modules/" > .gitignore
$ npm init -y
```

타입스크립트 세팅하기

```
$ npm i -D typescript
$ npx tsc --init // tsc config 파일 생성하기
$ npm i -D ts-node 
$ npx ts-node // 타입스크립트로 쓴 코드를 노드로 한번 컴파일을 해줘야함. 그렇지만 ts-node 를 사용하면 바로바로 사용할 수 있음.
```

Eslint 세팅하기

```
$ npm i -D eslint
$ npx eslint --init
  // typescript 로 사용하기 때문에 import/export 옵션으로 추가
```

nodemon 세팅하기

```
$ npm i -D nodemon
$ npx nodemon --init
```

nodemon 을 사용하는 이유는?

ts-node 로 서버를 실행하면 처음 실행 시 코드를 메모리에 저장하고 그 메모리에 저장된 값만 보여줌. 그래서 코드 수정이 발생하게 되면 다시 서버를 껐다가 켜야 하는 번거로움이 있는데 이걸 자동으로 실행해주는게 nodemon 임. 현재 프로젝트를 모니터링하고 변경사항이 있는 경우 자동으로 restart 하는 편이성을위해 개발환경에서만 사용함.

서버 실행시키기

```
$ nodemon app.ts
// 주의! ts-node 와 의존성이 존재하기 때문에 nodemon 으로 실행시키더라도 ts-node 패키지 의존이 필요함
```

### ![](<../.gitbook/assets/image (4).png>)

### 사용법

*







