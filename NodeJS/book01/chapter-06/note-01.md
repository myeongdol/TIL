## 6장 익스프레스 프로젝트 시작하기
### 익스프레스 프로젝트 시작하기
  ```javascript
  const express = require('express');

  const app = express();
  app.set('port', process.env.PORT || 3000);

  app.get('/', (req, res) => {
    res.send('Hello, Express');
  });

  app.listen(app.get('port'), () => {
    console.log(app.get('port'), '번 포트에서 대기 중');
  });
  ```
  * app.set('port', 포트), app.set(키, 값)
    + 서버가 실행될 포트를 설정
    + 키, 값을 통해 데이터 저장
  * app.get(주소, 라우터)
    + 주소에 대한 GET 요청 처리
    + GET 요청 외에도 POST, PUT, PATCH, DELETE, OPTIONS요청이 있다.
  * app.listen
    + 포트를 연결하고 서버를 실행

### 자주 사용하는 미들웨어
  * 미들웨는 익스프레스의 핵심
  * 요청과 응답의 중간에 위치하여 미들웨어라 부름
  * 요청과 응답을 조작하여 기능을 추가하기도 하고, 나쁜 요청을 걸러내기도 한다.
  * 미들웨어는 app.use와 함께 사용된다.
    ```javascript
    ...
    app.use((req, res, next) => {
      console.log('모든 요청에 다 실행됩니다.');
      next();
    });
    app.get('/', (req, res, next) => {
      console.log('GET / 요청에서만 실행됩니다.');
      next();
    }, (req, res) => {
      throw new Error('에러는 에러 처리 미들웨어로 갑니다.')
    });

    app.use((err, req, res, next) => {
      console.error(err);
      res.status(500).send(err.message);
    });
    ...
    ```
  * app.use에 매개변수가 req, res, next인 함수를 넣으면 된다.
  * 미들웨어는 위에서부터 아래로 순서대로 실행된다.
  * next를 사용 시 다음 미들웨어로 넘어간다.
  * 에러 처리 미들웨어는 매개변수가 반드시 네 개여야 합니다. (err, req, res, next)
    
    | 미들웨어가 실행되는 경우 |  |
    |:---|:---|
    |app.use(미들웨어)|모든 요청에서 미들웨어 실행|
    |app.user('/abc', 미들웨어)|abc로 시작하는 요청하는 미들웨어 실행|
    |app.post('/abc', 미들웨어)|abc로 시작하는 POST 요청에서 미들웨어 실행|
  * dotenv
    + dotenv 패키지는 .env 파일을 읽어서 process.env로 만든다.
    + 보안과 설정의 편의성을 위해 .env 파일로 관리하고 dotenv 패키지로 비밀 키를 로딩

### 자주 쓰는 미들웨어 패키지
  * morgan('인수')
    + 요청과 응답에 대한 정보를 콘솔에 기록
    + 인수로 dev, combined, common, short, tiny 넣을 수 있다.
    + [HTTP 메서드] [주소] [HTTP 상태 코드] [응답 속도] [응답 바이트] 출력
  * static
    + 정적인 파일들을 제공하는 라우터 역할
    + 파일을 발견했다면 다음 미들웨어는 실행되지 않고, 요청 경로에 해당 파일이 없으면 알아서 next 호출한다.
  * body-parser
    + 요청의 본문에 있는 데이터를 해석해서 req.body 객체로 만들어주는 미들웨어
    + 보통 폼 데이터나 AJAX 요청에 데이터를 처리한다. 단 멀티파트 데이터는 처리하지 못한다.
  * cookie-parser
    + 요청에 동봉된 쿠키를 해석해 req.cookies 객체로 만든다.
  * express-session
    + 세션 관리용 미들웨어로 데이터를 임시적으로 저장해둘 때 유용
  