# promise를 이용한 비동기처리

프로세스 상에 비동기처리를 해야할 일이 생겼습니다. </br>

1. 데이터 검사 </br>
  성공 -> 2.로 </br>
  실패 -> 중단
2. value 검사 (api call) </br>
  성공 -> logic_성공 </br>
  실패 -> logic_실패

### AS-IS
```javascript
processX() {
  if (!isValidData()) { // 1. 데이터 검사
    return false;
  }
  if (!isEqualValue()) { // 2. value 검사 (api call)
    logic_실패();
    return false;
  }
  logic_성공();
}

isEqualValue() {
  // api call
  $.get('api/v1/...', function(response) {
  });
}
```
value 검사 시 api call이 끝나기전에 logic_성공() 함수가 먼저 실행되고 login_실패()가 되어 문제가 발생했습니다. </br>
두 함수가 모두 실행되는 것은 말이안되기 때문에 Promise를 활용하여 비동기 처리를 해주었습니다.

### TO-BE
```javascript
processX() {
  if(!isValidData()) {
    return false;
  }
  isEqualValue().then(() => {
    logic_성공();
  }).catch(function(err) {
    console.log(err);
    logic_실패();
  });
}

isEqualValue() {
  return new Promise((resolve, reject) => {
    // api call
    $.get('api/v1/...', function(response) {
      if(response) {
        resolve();
      }
      reject();
    });
  });
}
```

### 참고 </br>
https://joshua1988.github.io/web-development/javascript/promise-for-beginners/#promise%EA%B0%80-%EB%AD%94%EA%B0%80%EC%9A%94
