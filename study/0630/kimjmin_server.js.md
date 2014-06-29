#server.js 설명.

- `use strict` : strict 모드는 코드에 더 나은 오류 검사를 적용하는 방법. strict 모드를 사용하면, 예를 들어 암시적으로 선언한 변수를 사용하거나 읽기 전용 속성에 값을 할당하거나 확장할 수 없는 개체에 속성을 추가할 수 없음.
- 모듈 선언 :

```
var mongoose = require('mongoose'),
    passport = require('passport'),
    logger = require('mean-logger');
```
  -  mongoos : 몽고 DB 사용을 위한 모듈.
  - passport : Node.JS 에서 OAuth 등을 사용하기 위해 필요.
  - logger : 로깅 묘듈.

- 몽고DB 연결.

```
var config = require('./server/config/config');
var db = mongoose.connect(config.db);
```
  - ./server/config/config.js 파일 연결.

```
// Set the node environment variable if not set before
process.env.NODE_ENV = ~fs.readdirSync('./server/config/env').map(function(file) {
    return file.slice(0, -3);
}).indexOf(process.env.NODE_ENV) ? process.env.NODE_ENV : 'development';

// Extend the base configuration in all.js with environment
// specific configuration
module.exports = _.extend(
    require('./env/all'),
    require('./env/' + process.env.NODE_ENV) || {}
);
```
  - ./server/config/env/all.js

```
module.exports = {
        root: rootPath,
        port: process.env.PORT || 3000,
        hostname: process.env.HOST || process.env.HOSTNAME,
        db: process.env.MONGOHQ_URL,
        templateEngine: 'swig',
```

- express 모듈 로딩
```
// Bootstrap Models, Dependencies, Routes and the app as an express app
var app = require('./server/config/system/bootstrap')(passport, db);

// Start the app by listening on <port>, optional hostname
app.listen(config.port, config.hostname);
console.log('Mean app started on port ' + config.port + ' (' + process.env.NODE_ENV + ')');
```

- 로깅 시작

```
// Initializing logger
logger.init(app, passport, mongoose);
```
- express 모듈 실행.
```
// Expose app
exports = module.exports = app;
```

## 모듈 로딩 & 내보내기

- `require('모듈명')` : 해당 모듈명 로딩
- `require('경로/파일명')` : 해당 js 파일을 로딩. .js 확장자 생략.

  예) `var config = require('./server/config/config');` : ./server/config/config.js 파일을 로드.

- `module.exports = app;` : app 이라는 이름의 모듈 내보내기.
