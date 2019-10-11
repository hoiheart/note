# 기초

### 타입

자바스크립트의 타입 구조도는 다음과 같다.

* String \(primitive\)
* Number \(primitive\)
* Boolean \(primitive\)
* Null \(primitive\)
* Undefined \(primitive\)
* Symbol \(primitive\)
* Object _**\(reference\)**_
  * Function
  * Array
  * Date
  * RegExp
  * Map, WeakMap
  * Set, WeakSet

### 변수

var, let, const 를 사용하여 값을 선언하며, 값을 프로그램 안에서 직접 지정하는 방식을 리터럴이라 한다.

```javascript
var obj = {
    name: "animation",
    "slide-up": true,
    callback: function() {
        return 'callback';
    }
}
```

* 식별자 : 상수, 변수, 함수 등의 이름
* 프로퍼티 : 객체의 키와 값으로 구성된 데이터
* 메소드 : 객체의 기능 역할을 하는 값 \(ex: function\)

