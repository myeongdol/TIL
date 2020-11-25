## 3장 노드 기능 알아보기
* 노드 내장 모듈 사용하기
  + [os](https://nodejs.org/api/os.html)
    - 노드는 os 모듈에 정보가 담겨 있다.
  + [path](https://nodejs.org/api/path.html)
    - 폴더와 파일의 경로를 쉽게 조작하도록 도와주는 모듈
  + [url](https://nodejs.org/api/url.html)
    - 인터넷 주소를 쉽게 조작하도록 도와주는 모듈
  + [querystring](https://nodejs.org/api/querystring.html)
  + [crypto](https://nodejs.org/api/crypto.html)
    - 다양한 방식의 암호화를 도와주는 모듈
    - 단방향 함호화
      - 복호화 할 수 없는 암호화 방식
    - 양방향 암호화
      - 암호화된 문자열을 복호화 할 수 있음
  + [util](https://nodejs.org/api/util.html)
    - 각종 편의 기능을 모아둔 모듈
  + [worker_threads](https://nodejs.org/api/worker_threads.html)
    - 노드에서 멀티 스레드 방식으로 작업할 수 있다.
  + [child_process](https://nodejs.org/api/child_process.html)
    - 노드에서 다른 프로그램을 실행하고 싶거나 명령어를 수행하고 싶을 때 사용하는 모듈
  + 기타 모듈들
    - assert
      - 값을 비교하여 동작여부 테스트
    - dns
      - 도메인 이름에 대한 IP 주소를 얻는데 사용
    - net
      - HTTP보다 로우 레벨인 TCP나 IPC 통신을 할 때 사용
    - string_decoder
      - 버퍼 데이터를 문자열로 변경 시 사용
    - tls
      - TLS와 SSL에 관련된 작업에 사용
    - tty
      - 터미널과 관련된 작업에 사용
    - dgram
      - UDP와 관련된 작업에 사용
    - v8
      - v8 엔진에 직접 접근할 때 사용
    - vm
      - 가상 머신에 직접 접근 할 때 사용
