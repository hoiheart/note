# 호이스팅, 스코프, 클로저

### 호이스팅

변수 및 함수 선언이 코드의 상단으로 올려지는 것

```javascript
message("hello");

function message(str) {
  console.log("Messege is " + str); // Message is hello
}
```

### 스코프

변수들이 영향을 끼치는 범위로 전역 스코프와 지역 스코프로 나뉜다.  
지역 스코프는 함수 스코프와 지역 스코프가 존재한다.

### 변수 선언에 따른의 스코프, 호이스팅 차이

#### 변수 생성 과정

* 선언: 실행 컨텍스트의 변수 객체에 등록
* 초기화: 변수 객체 메모리 할당 및 undefined 초기화
* 할당: 변수에 값 할당

#### var

var의 스코프는 함수 스코프이며 호이스팅은 선언 및 초기화까지 이루어진다.

```javascript
var x = 'outer scope';

(function() {
  console.log(x); // undefined
  var x = 'inner scope';
}());
```

#### let, const

let의 스코프는 블록 스코프이며 호이스팅은 선언까지만 이루어진다.  
이를 일시적 사각 지대 TDZ\(Temporal Dead Zone\)라 한다.

```javascript
let x = 'outer scope';

{
  console.log(x); // ReferenceError
  let x = 'inner scope';
};
```

#### TDZ

변수는 그들의 어휘적 환경에 포함될 때 생성되지만, 어휘적 바인딩이 실행되기 전까지는 액세스할 수 없다.  
이는 디폴트 파라미터나 Class 에서도 적용된다.

[참고 블로그](https://medium.com/korbit-engineering/let%EA%B3%BC-const%EB%8A%94-%ED%98%B8%EC%9D%B4%EC%8A%A4%ED%8C%85-%EB%90%A0%EA%B9%8C-72fcf2fac365)

### 클로저

함수를 선언할 때 만들어지는 유효범위가 사라진 후에도 호출할 수 있는 함수  
\(어떤 함수 A에서 선언한 변수 a를 참조하는 내부함수 B를 외부로 전달할 경우 A의 실행 컨텍스트가 종료된 이후에도 변수 a가 사라지지 않는 현상\)

```javascript
// inner function
var outer = function () {
  var a = 1;
  var inner = function () {
    return ++a;
  };
  return inner;
};
var outer2 = outer();
console.log(outer2()); // 2
console.log(outer2()); // 3

// setInterval
(function () {
  var a = 0;
  var intervalId = null
  var inner = function () {
    if (++a >= 10) {
      clearInterval(intervalId);
    }
    console.log(a);
  };
  intervalId = setInterval(inner, 1000)
})();

// eventListener
(function () {
  var counte = 0;
  var button = document.createElement('button');
  button.innertext = 'click';
  button.addEventListener('click', function () {
    console.log(++count, 'times clicked');
  })
  document.body.appendChild(button)
})();
```

{% hint style="info" %}
클로저의 메모리 소모\(개발자 의도이므로 누수의 표현은 적절치 않음\)는 본질적인 특성일 뿐이며, 함수형 프로그래밍의 보편적 개념이기 때문이 이를 정확히 이해하고 활용하는 것이 중요하다.  
클로저가 더 이상 필요가 없을 때 식별자에 null 할당을 통해 관리해주면 GC에서 자동으로 수거한다.
{% endhint %}



