# 2020-11-08 TIL

## 2장 알아두어야 할 자바스크립트

### const, let
  * const
    + 초기화할 때 값을 할당하지 않으면 에러 발생
    + 한번 값을 할당하면 다른 값 할당 불가
  * let
    + 초기화시 값을 할당 하지 않아도된다.
    + 한번 값을 할당해도 변경 가능하다.

### 템플릿 문자열
  ```javascript
  const num1 = 1;
  const num2 = 2;
  const result = 3;
  const string = `${num1} 더하기 ${num2}는 '${result}'`
  console.log(string);  // 1 더하기 2는 '3'
  ```

### [구조분해 할당](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
  ```javascript
  var array = {'nodejs', {}, 10, true};
  var node = array[0];
  var obj = array[1];
  var bool = array[3];

  // 구조분해 할당
  const array = ['nodejs', {}, 10, true];
  const [node, obj, , bool] = array;
  // 코드 줄 수를 상당히 줄여주므로 유용
  ```
### [클래스](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classess)
  ```javascript
  // 클래스 기반 코드 예제
  class Human {
    constructor(type = 'human') {
      this.type = type;
    }

    static isHuman(human) {
      return human instanceof Human;
    }

    breathe() {
      alert('h-a-a-a-m');
    }
  }

  class Zero extends Human {
    constructor(type, firstName, lastName) {
      super(type);
      this.firstName = firstName;
      this.lastName = lastName;
    }

    sayName() {
      super.breathe();
      alert(`${this.firstName} ${this.lastName}`);
    }
  }

  const newZero = new Zero('human', 'Zero', 'Cho');
  Human.isHuman(newZero);  // true
  // 클래스 문법으로 바뀌었더라도 자바스크립트는 프로토타임 기반으로 동작
  ```

### 프로미스 ([Promise](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise))
  * ES2015부터는 자바스크립트와 노드의 API들이 콜백 대신 프로미스로 재구성되어 콜백 지옥 현상을 극복
  ```javascript
  const condition = true;
  // 프로미스 객체 생성
  const promise = new Promise((resolve, reject) => {
    if (condition) {
      resolve('성공');
    } else {
      reject('실패');
    }
  });

  promise
    .then((message) => {
      console.log(message);  // 성공(resolve)한 경우 실행
    })
    .catch((error) => {
      console.error(error); // 실패(reject)한 경우 실행
    })
    .finally(() => {  // 끝나고 무조건 실행
      console.log('무조건 실행');
    })
  ```
  * Promise.all
  ```javascript
  const promise1 = Promise.resolve('성공1');
  const promise2 = Promise.resolve('성공2');
  Promise.all([promise1, promise2])
    .then((result) => {
      console.log(result);  // ['성공1', '성공2'];
    })
    .catch((error) => {
      console.error(error);
    });
  ```
### [async](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/async_function) / [await](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/await)
  ```javascript
  async function findAndSaveUser(Users) {
    try {
      let user = await Users.findOne({});
      // await Users.findOne({}) 이 resolve될 때까지 기다린 다음 user 변수를 초기화한다.
      User.name = 'zero';
      user = await user.save();
      user = await Users.findOne({ gender: 'm'});
    } catch (error) {
      console.log(error);
    }
  }
  ```

### AJAX
  * 비동기적 웹 서비스를 개발할 때 사용하는 기법
  ```javascript
  // axios GET 요청 예제
  axios.get('https://www.zerocho.com/api/get')
    .then((result) =>) {
      console.log(result);
      console.log(result.data);  // {}
    }
    .catch((error) => {
      console.error(error);
    });

  // axios POST 요청 예제
  axios.post('https://www.zerocho.com/api/post/json', {
      name: 'zerocho',
      birth: 1994,
    })
    .then((result) =?) {
      console.log(result);
      console.log(result.data);  // {}
    }
    .catch((error) => {
      console.error(error);
    });
  ```

### [FormData](https://developer.mozilla.org/ko/docs/Web/API/FormData)
  * HTML form 태그의 데이터를 동적으로 제어할 수 있는 기능

### [encodeURIComponent](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent), [decodeURIComponent](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/decodeURIComponent)
  * 서버가 한글 주소를 이해하지 못하는 경우에 사용

### [데이터 속성과 dataset](https://developer.mozilla.org/ko/docs/Web/API/HTMLElement/dataset)