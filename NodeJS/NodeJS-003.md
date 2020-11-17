## 3장 노드 기능 알아보기
* REPL
  + 노드도 콘솔을 제공하는데, 입력한 코드를 읽고(Read), 해석하고(Eval), 결과물을 반화하고(Print), 종료할 때까지 반복(Loop)

* 모듈로 만들기
  
  ```javascript
  // var.js
  const add = '홀수입니다';
  const even = '짝수입니다';

  module.exports = {
    odd,
    even,
  };
  ```

  ```javascript
  // func.js
  const { odd, even } = require('./var');

  function checkOddOrEven(num) {
    if(num % 2) { // 홀수 일 때
      return odd;
    }
    return even;
  }

  module.exports = checkOddOrEven;
  ```
  
  ```javascript
  // index.js
  const { odd, even } = require('./var');
  const checkNumber = require('./func');

  function checkStringOddOrEven(str) {
    if(str.length % 2) { // 홀수 일 떄
      return odd;
    }
    return even;
  }

  console.log(checkNumber(10));
  console.log(checkStringOddOrEven('hello'));
  ```

  ```
  $ node index
  짝수입니다
  홀수입니다
  ```

  * ES2015 모듈
  ```javascript
  // func.mjs
  import { odd, even } from './var';

  function checkOddOrEven(num) {
    if (num % 2) { // 홀수면
      return odd;
    }
    return even;
  }

  export default checkOddOrEven;
  ```