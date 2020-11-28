## 5장 패키지 매니저
### npm
  * Node Package Manager, 노드 패키지 매니저
  * yarn은 페이스북이 내놓은 패키지 매니저

### package.json
  * packge name
    - 패키지의 이름
  * version
    - 패키지의 버전
  * entry point
    - 자바스크립트 실행 파일 진입점
  * test command
    - 코드를 테스트할 때 입력할 명령어를 의미한다.
    - package.json scripts 속성 안의 test 속성에 저장된다.
  * git repository
    - 코드를 저장해둔 깃 저장소 주소를 의미한다.
  * keywords
    - npm 공식 홈페이지에서 패키지를 쉽게 찾을 수 있도록 해준다.
  * license
    - 해당 패키지의 라이선스

### [nvm](https://nodejs.org/ko/download/package-manager/#nvm)
  * Node Version Manager는 Node.js의 다양한 릴리스 버전을 관리하는 bash 스크립트

### [npm install](https://docs.npmjs.com/cli/v6/commands/npm-install)
  * node_modules 폴더는 삭제를 해도 npm install 명령어 실행 시 package.json에 저장된 정보를 통해 다시 생성된다.

### [npm audit](https://docs.npmjs.com/cli/v6/commands/npm-audit)
  * 패키지의 알려진 취약점을 검사할수 있는 명령어
  * npm audit fix
    + 스스로 수정할 수 있는 취약점을 알아서 수정

### 패키지 버전 이해하기
  * 버전의 첫 번째 자리는 major 버전
    + 0이면 초기 개발 중, 1부터는 정식 버전
    + 하의 호환이 되지 않는 변경 사항

  * 버전의 두 번째 자리는 minor 버전
    + 하위 호환이 되는 변경 사항

  * 버전의 세 번째 자리는 patch 버전
    + 간단한 버그 수정

### [npm-outdated](https://docs.npmjs.com/cli/v6/commands/npm-outdated)
  * 업데이트할 수 있는 패키지가 있는 확인 가능

### [npm-uninstall](https://docs.npmjs.com/cli/v6/commands/npm-uninstall)

### [npm-search](https://docs.npmjs.com/cli/v6/commands/npm-search)

### [npm-adduser](https://docs.npmjs.com/cli/v6/commands/npm-adduser)
  * 패키지를 배포할 때 로그인 기능
  * [npm whoami](https://docs.npmjs.com/cli/v6/commands/npm-whoami)
  * [npm logout](https://docs.npmjs.com/cli/v6/commands/npm-logout)

### [npm-publish](https://docs.npmjs.com/cli/v6/commands/npm-publish)