# 보안

## 프론트엔드 보안

웹 보안에 있어서 원천적으로는 서버와 DB단에서 처리가 필수로 되어야 하겠지만, 최근 웹앱은 프론트엔드에서 직접 서버와 통신을 하는 경우가 많고 다양한 공격들이 프론트엔드 단에서 이루어지고 있기 때문에 이에 대한 이해 및 1차적인 방어 처리가 필요하다.

### 

### Eval

> **`eval()`**은 문자로 표현된 JavaScript 코드를 실행하는 함수입니다.
>
>  `eval()`은 인자로 받은 코드를 caller의 권한으로 수행하는 위험한 함수입니다. 악의적인 영향을 받았을 수 있는 문자열을 `eval()`로 실행한다면, 당신의 웹페이지나 확장 프로그램의 권한으로 사용자의 기기에서 악의적인 코드를 수행하는 결과를 초래할 수 있습니다. 또한, 제3자 코드가 `eval()`이 호출된 위치의 스코프를 볼 수 있으며, 이를 이용해 비슷한 함수인 [`Function`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function)으로는 실현할 수 없는 공격이 가능합니다.

### 

### CORS \(Cross-Origin Resource Sharing\)

> Cross-Origin Resource Sharing 표준은 웹 브라우저가 사용하는 정보를 읽을 수 있도록 허가된 출처 집합를 서버에게 알려주도록 허용하는 HTTP 헤더를 추가함으로써 동작합니다. 추가적으로, 사용자 데이터 상에서 부수 효과를 일으킬 수 있는 HTTP 요청 메서드에 대해\(특히, {HTTPMethod\("GET"\)}} 이외의 HTTP 메서드들 혹은 어떤 MIME 타입을 사용하는  {HTTPMethod\("POST"\)}} 사용에 대해\), 스펙은 브라우저가 요청을 "preflight"\(사전 전달\)하도록 강제하는데, 이는 HTTP [`OPTIONS`](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods/OPTIONS) 요청 메서드를 이용해 서버로부터 지원 중인 메서드들을 내려 받은 뒤, 서버에서 "approval"\(승인\) 시에 실제 HTTP 요청 메서드를 이용해 실제 요청을 전송하는 것을 말합니다. 서버들은 또한 클라이언트에게 \(Cookie와 HTTP Authentication 데이터를 포함하는\) "credentials"가 요청과 함께 전송되어야 하는지를 알려줄 수도 있습니다.

#### Headers

```text
Access-Control-Allow-Origin: <origin> | *
Access-Control-Allow-Credentials: true | false // 인증을 통한 요
Access-Control-Allow-Methods: <method>[, <method>]*
```

### 

### CSP \(Content Security Policy\)

Headers의 Content-Security-Policy 정책을 이용하여 허용된 소스만을 실행시켜 XSS 취약점을 방어

#### whitelist 방식

```text
Content-Security-Policy: script-src 'self' https://apis.google.com
```

```javascript
<script src="https://apis.google.com/api.js"></script>
```

#### nonce 방식

```text
Content-Security-Policy: script-src 'nonce-EDNnf03nceIOfn39fn3e9h3sdfa'
```

```javascript
<script nonce=EDNnf03nceIOfn39fn3e9h3sdfa>
  //Some inline code I cant remove yet, but need to asap.
</script>
```

### 

### Prototype 오염

> 객체 리터럴의 **proto**는 Object.prototype과 같다는 것을 이용해 다른 객체 속성에 영향을 주는 방식

[lodash 사례 참고](https://blog.coderifleman.com/2019/09/19/prototype-pollution-attacks-in-nodejs/)



### Tabnabbing

> HTML 문서 내에서 링크\(target이 \_blank인 Anchor 태그\)를 클릭 했을 때 새롭게 열린 탭\(또는 페이지\)에서 기존의 문서의 location을 피싱 사이트로 변경해 정보를 탈취하는 공격 기술

[이메일 서비스 공격 참고](https://blog.coderifleman.com/2017/05/30/tabnabbing_attack_and_noopener/)

###  innerHTML

React나 Vue 등의 자바스크립트 라이브러리는 html 문법을 자동으로 escape 해주며, 필요할 경우 dangerouslySetInnerHTML, v-html 등으로 innerHTML의 역할을 수행한다.

> 웹사이트에서 임의의 HTML을 동적으로 렌더링하려면 [XSS 취약점](https://en.wikipedia.org/wiki/Cross-site_scripting)으로 쉽게 이어질 수 있으므로 매우 위험할 가능성이 있습니다. 신뢰할 수 있는 콘텐츠에서만 HTML 보간을 사용하고 사용자가 제공한 콘텐츠에서는 **절대** 사용하면 안됩니다.



### CSRF \(Cross-Site Request Forgery\)

세션 및 쿠키를 통한 사용자의 권한을 이용해 해당 웹사이트를 공격하는 행위

* Referrer 검증, Security Token 사용 등 추가 작업을 통한 방어
* Cookie 설정을 SameSite=Lax 이상으로 설정 \(Privacy 침해에도 대응 효과\)

