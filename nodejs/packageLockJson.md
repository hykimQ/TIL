# package-lock.json

- package-lock.json은 npm을 사용하여 package.json 또는 node_modules 트리를 수정하면 자동으로 생성
- 파일이 생성되는 시점의 의존성 트리에 대한 정보를 가짐
- package.json에는 version range가 사용됨(특정버전이 아닌 버전의 범위)
- package.json에 ^4.16.3이 있고 npm i를 실행하면 4.16 이나 업데이트 된 버전이 설치 될 수 있음

1. package-lock.json은 의존성 트리에 대한 정보를 가지고 작성된 시점의 의존선 트리가 다시 생성될 수 있도록 보장
2. package-lock.json은 저장소에 같이 commit
3. package-lock.json은 node-modules없이 배포하는 경우 반드시 필요

> [참고자료](https://hyunjun19.github.io/2018/03/23/package-lock-why-need/)
