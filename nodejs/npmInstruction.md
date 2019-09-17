# npm 명령어

### 프로젝트 생성

- npm init 현재 디렉토리에 NPM 기반으로 프로젝트를 생성
- -y, --yes 디폴트로 생성

```console
$ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (hello-npm)
version: (1.0.0)
description:
```

### 신규 패키지 설치

- npm install, npm i (커맨드 뒤 패키지 이름을 붙이지 않으면 기존 패키지를 일괄적으로 설치)
- --save-dev, -D 개발의존성 모드로 설치
- --global, -g 패키지 전역 설치

```console
$ npm i lodash
+ lodash@4.17.10
added 1 package from 2 contributors and audited 1 package in 0.914s
found 0 vulnerabilities

$ npm i -D mocha

$ npm i -g http-server
```

### 설치된 패키지 확인

- npm install, npm i (커맨드 뒤 패키지 이름을 붙이지 않으면 기존 패키지를 일괄적으로 설치)
- --save-dev, -D 개발의존성 모드로 설치
- --global, -g 패키지 전역 설치

```console
$ npm ls
```

### 패키지 제거

- npm uninstall, npm r

```console
$ npm r mocha
```

### 패키지 무설치 실행 (NPX)

- npx
- 패키지를 프로젝트나 전역에 설치하지 않고 다음과 같이 npx 커맨드 뒤에 패키지명만 붙여서 실행

```console
$ npx http-server
npx: installed 25 in 3.28s
Starting up http-server, serving ./
Available on:
  http://127.0.0.1:8080
  http://10.212.5.70:8080
Hit CTRL-C to stop the server
```

### 스크립트 실행

- npx
- 패키지를 프로젝트나 전역에 설치하지 않고 다음과 같이 npx 커맨드 뒤에 패키지명만 붙여서 실행
- test, start는 run생략 가능

```console
$ npm run build

$ npm test

$ npm start
```
