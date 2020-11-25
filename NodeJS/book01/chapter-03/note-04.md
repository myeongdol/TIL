## 3장 노드 기능 알아보기
* 파일 시스템 접근하기
  + [fs 모듈](https://nodejs.org/api/fs.html)은 파일 시스템에 접근하는 모듈
  ```javascript
  // readme.txt
  저를 읽어주세요.
  ```
  ```javascript
  const fs = require('fs');
  fs.readFile('/.readme.txt', (err, data) => {
    if (err) {
      throw err;
    }
    console.log(data);  // <Buffer ex a0 80 ...>
    console.log(data.toString());  // 저를 읽어주세요.
    // readFile의 결과물은 버퍼(Buffer)라는 형식으로 제공된다.
  })
  ```
  + readFileSync는 동기 방식으로 파일을 읽는다.

* 버퍼와 스트림 이해하기
  + 버퍼링
    - 영상을 재생할 수 있을 때까지 데이터를 모으는 동작
  + 스트리밍
    - 방송인의 컴퓨터에서 시청자의 컴퓨터로 영상 데이터를 조금씩 전송하는 동작
  ```javascript
  const buffer = Buffer.from('저를 버퍼로 바꿔보세요');
  console.log('from():', buffer);
  console.log('length:', buffer.length);
  console.log('toString():', buffer.toString());

  const array = [Buffer.from('띄엄 '), Buffer.from('띄엄 '), Buffer.from('띄어쓰기')];
  const buffer2 = Buffer.concat(array);
  console.log('concat():', buffer2.toString());

  const buffer3 = Buffer.alloc(5);
  console.log('alloc():', buffer3);
  ```
  ```javascript
  $node buffer
  from(): <Buffer ec a0 80 ...>
  length: 32
  toString(): 저를 버퍼로 바꿔보세요
  concat(): 띄엄 띄엄 띄어쓰기
  alloc(): <Buffer 00 00 00 00 00>
  ```
  + Buffer
    - from(문자열)
      - 문자열을 버퍼로 변경 가능
    - toString(버퍼)
      - 버퍼를 다시 문자열로 변경 가능
    - concat(배열)
      - 배열 안에 든 버퍼들을 하나로 합칩니다.
    - alloc(바이트)
      - 빈 버퍼를 생성, 바이트를 인수로 넣으면 해당 크기의 버퍼가 생성된다.
  
  + createReadStream
  ```javascript
  // readme3.txt
  저는 조금씩 조금씩 나눠서 전달됩니다. 나눠진 조각을 chunk라고 부릅니다.
  ```

  ```javascript
  const fs = require('fs');
  
  const readStream = fs.createReadStream('./readme3.txt', { highWaterMark: 16 });
  const data = [];

  readStream.on('data', (chunk) => {
    data.push(chunk);
    console.log('data :', chunk, chunck.length);
  });

  readStream.on('end', () => {
    console.log('end :', Buffer.concat(data).toString());
  });

  readStream.on('error', (err) => {
    console.log('error :', err);
  });
  ```
  ```javascript
  $node createReadStream
  data : <Buffer ec a0 ...> 16
  data : <Buffer 20 ec ...> 16
  data : <Buffer a0 ec ...> 16
  data : <Buffer 88 eb...> 16
  data : <Buffer ec a1 ...> 16
  data : <Buffer 9d bc ...> 16
  data : <Buffer 8b a4 2e> 3
  end : 저는 조금씩 조금씩 나눠서 전달됩니다. 나눠진 조각을 chunk라고 부릅니다.
  ```

  + createWhiteStream
  ```javascript
  // readme4.txt
  저를 writeme3.txt로 보내주세요.
  ```
  ```javascript
  // pipe.js
  const fs = require('fs');

  const readStream = fs.createReadStream('readme4.txt');
  const writeStream = fs.createwriteStream('writeme3.txt');
  readStream.pipe(writeStream);
  ```
  ```javascript
  $node pipe
  // readme4.txt와 똑같은 내용의 writeme3.txt가 생성
  ```

  + gzip
    - 파일을 압축하는 모듈
