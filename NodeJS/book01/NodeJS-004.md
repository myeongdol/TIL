## 3장 노드 기능 알아보기
* 노드 내장 객체 알아보기
  + global
    - 브라우저의 window와 같은 전역 객체
    - console 객체도 원래는 global.console이다.

  + console
    - 디버깅을 위해 사용
    - console.time(레이블)
      - time과 timeEnd 사이의 시간을 측정
    - console.log(내용)
      - 평범한 로그를 콘솔에 표시
    - console.error(에러 내용)
      - 에러를 콘솔에 표시
    - console.table(배열)
      - 배열의 요소로 객체 리터럴을 넣으면, 객체의 속성들이 테이블 형식으로 표현
    - console.dir(객체, 옵션)
      - 객체를 콘솔에 표시할 때 사용한다. 옵션에는 colors, depth를 사용
    - console.trace(레이블)
      - 에러가 어디서 발생헀는지 추적
  
  + 타이머
    - setTimeout(콜백 함수, 밀리초)
      - 주어진 밀리초 이후에 콜백 함수 실행
    - setInterval(콜백 함수, 밀리초)
      - 밀리초마다 콜백 함수를 반복 실행
    - setImmediate(콜백 함수)
      - 콜백 함수를 즉시 실행
    - clearTimeout(아이디), clearInterval(아이디), clearImmediate(아이디)
      - 해당 함수 취소
  
  + __filename, __dirname
    ```javascript
    $ node filename.js
    C:\Users\zerocho\filename.js  // __filename
    C:\Users\zerocho  // __dirname
    ```
  
  + module, exports, require
    - module.exports와 exports가 같은 객체를 참조

  + process
    - 현재 실행되고 있는 노드 프로세스에 대한 정보를 담고있다.
    ```javascript
    $ node
    > process.version
    v14.0.0  // 설치된 노드의 버전입니다.
    > process.arch
    x64  // 프로세서 아키텍처 정보입니다.
    > process.platform
    win32  // 운영체제 플랫폼 정보입니다.
    > process.pid
    14736  // 현재 프로세스의 아이디입니다.
    > process.uptime()
    199.36  // 프로세스가 시작된 후 흐른 시간입니다.
    > process.execPath
    C:\\Program Files\\nodejs\\node.exe  // 노드의 경로입니다.
    > process.cwd()
    C:\\Users\\zerocho  // 현재 프로세스가 실행되는 위치입니다.
    > process.cpuUsage()
    { user: 390000, system: 203000 }  // 현재 cpu 사용량입니다.
    ```
    - process.env
      - 시스템의 환경 변수
    
    - process.nextTick(콜백)
      - 이벤트 루프가 다른 콜백 함수들보다 nextTick의 콜백 함수를 우선으로 처리
      - setImmediate, setTimeout보다 먼저 실행
      - process.nextTick(), Promise를 마이크로태스크라고 따로 구분지어 부른다.

    - proces.exit(코드)
      - 실행 중인 노드 프로세스를 종료한다.