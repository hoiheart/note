# 문 및 선언

### 제어문

#### 블록

0개 이상의 구문을 묶을 때 사용

```text
{
  StatementList
}
```

#### if... else

지정한 조건이 참인 경우 명령문\(statement\)을 실행

```text
if (condition)
   statement1
[else
   statement2]
```

#### switch

조건 하나로 여러가지 중 하나를 선택하여 처리

```text
switch (expression) {
  case value1:
    //Statements executed when the
    //result of expression matches value1
    [break;]
  ...
  case valueN:
    //Statements executed when the
    //result of expression matches valueN
    [break;]
  [default:
    //Statements executed when none of
    //the values match the value of the expression
    [break;]]
}
```

#### while

조건문이 참일 때 실행되는 반복문이다. 조건은 문장안이 실행되기 전에 참, 거짓을 판단

```text
while (condition)
  statement
```

#### do...while

시작하면서 조건을 검사하지 않고 마지막에 검사  
루프 바디를 최소 한번 실행하려 할 때 사용

```text
do
   statement
while (condition);
```

#### for

괄호로 감싸고 세미콜론으로 구분한 세 개의 선택식과, 반복을 수행할 문\(주로 블럭문\)으로 이루어짐

```text
for ([initialization]; [condition]; [final-expression])
   statement
```

#### for ... in

객체의 모든 non-Symbol, enumerable properties을 반복

```javascript
for (variable in object) {
    // 상속된 속성도 포함되므로 다음 조건문을 사용하는 것을 권장
    if( obj.hasOwnProperty( prop ) ) {}
}
```

#### for ... of

이터러블 객체 \(Array, Map, Set, String, TypedArray, arguments 객체 등을 포함\)에 대해서 반복 \(컬렉션 전용\)

```text
for (variable of iterable) {
  statement
}
```

#### 예외처리

* break: 루프 중간에 빠져나감
* continue: 다음 루프로 바로 건너뜀
* return: 제어문을 무시하고 현재 함수를 즉시 빠져나감
* throw: 예외를 발생하고 핸들러로 처리

