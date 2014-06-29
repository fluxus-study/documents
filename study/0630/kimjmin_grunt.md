#grunt 설명.

`grunt` 명령은 `Gruntfile.js` 파일에 기록된 내용을 실행함.

## MEAN 에서 grunt 실행.

### Gruntfile.js 설명

[설명](http://blog.outsider.ne.kr/892)

[Gruntfile.js](https://github.com/fluxus-study/kimjmin/blob/master/Gruntfile.js)

- `module.exports = function(grunt){ }` 으로 전체 소스 묶어줌.
- `grunt.initConfig({ });` : 딱 한번만 와야 함.
- `pkg:` : 패키지 파일. package.json.
- `watch:` : watch는 files에 지정된 파일들의 변경사항을 감시하다가 변경사항이 발생하면 tasks에 지정된 동작을 실행함.
```
watch: {
  js: {
    files: paths.js,
    tasks: ['jshint'],
    options: {
      livereload: true
    }
  },
```
`paths.js` 는 상단에 `var paths = {` 에서 지정한 `js: []` 파일들
- [jshint](http://www.jshint.com/docs/) : 자바스크립트 코드 검사 도구. [설명](http://blog.outsider.ne.kr/1007)
- `uglify` : 자바스크립트 compressor/minifier 해 주는 모듈인듯.
- [csslint](http://csslint.net/) : 마찬가지로 css minifier 해 주는 모듈인듯.
- `nodemon` : 오토 디플로이 하는 녀석인듯.
- [karma](https://egghead.io/lessons/unit-testing-introduction-to-karma) : 앵귤러랑 같이 사용되는 녀석인듯.

grunt 명령어 실행하면 //Default task(s) 부분 실행.
