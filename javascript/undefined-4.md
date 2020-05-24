# 자료구조와 알고리즘

### 자료 구조

#### List

순서가 있는 집합

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#xAD6C;</th>
      <th style="text-align:left"></th>
      <th style="text-align:left">&#xC7A5;&#xC810;</th>
      <th style="text-align:left">&#xB2E8;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Array List</td>
      <td style="text-align:left">&#xC804;&#xCCB4; &#xAC2F;&#xC218;&#xAC00; &#xC815;&#xD574;&#xC838; &#xC788;&#xC74C;</td>
      <td
      style="text-align:left">&#xC811;&#xADFC;&#xC774; &#xBE60;</td>
        <td style="text-align:left">
          <p>&#xB3D9;&#xC801;&#xC778; &#xBA54;&#xBAA8;&#xB9AC; &#xD560;</p>
          <p>&#xB370;&#xC774;&#xD130; &#xBCC0;&#xD615;&#xC5D0; &#xBD88;&#xB9AC;</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">Linked List</td>
      <td style="text-align:left">&#xB2E4;&#xC74C; &#xAC12;&#xC758; &#xC8FC;&#xC18C;&#xB97C; &#xD3EC;&#xC778;&#xD130;&#xB85C;
        &#xC5F0;</td>
      <td style="text-align:left">
        <p>&#xD544;&#xC694;&#xD55C; &#xB9CC;&#xD07C;&#xB9CC; &#xBA54;&#xBAA8;&#xB9AC;
          &#xD560;&#xB2F9;</p>
        <p>&#xC790;&#xB8CC;&#xC758; &#xBCC0;&#xD615;&#xC5D0; &#xC720;</p>
      </td>
      <td style="text-align:left">
        <p>&#xD3EC;&#xC778;&#xD130;&#xB85C; &#xC778;&#xD55C; &#xC800;&#xC7A5; &#xACF5;&#xAC04;
          &#xB0AD;&#xBE44;</p>
        <p>&#xD2B9;&#xC815; &#xC790;&#xB8CC; &#xD0D0;&#xC0C9; &#xC2DC;&#xAC04;&#xC774;
          &#xB9CE;&#xC774; &#xC18C;&#xBAA8;</p>
      </td>
    </tr>
  </tbody>
</table>### 빅오 표기법

빅오 표기법은 알고리즘의 최악의 경우 복잡도를 측정한다.  
"n이 무한으로 접근할 때 무슨 일이 일어날까"를 고려해야 한다.

![](../.gitbook/assets/68747470733a2f2f6170656c6261756d2e66696c65732e776f726470726573732e636f6d2f323031312f31302f796161636f.jpg)

#### 시간 복잡도 호칭

* O\(1\) : 상수 시간
* O\(n\) : 선형 시간
* O\(n²\) : 2차 시간
* O\(n³\) : 3차 시간
* O\(㏒ n\) : 로그 시간

#### 빅오 표기법 법칙

**계수 법칙**

크기와 연관되지 않은 상수를 전부 무시한다.

```javascript
function a(n) {
  var count = 0;
  for (var i = 0; i < 5 * n; i++) {
    count += 1;
  }
  return count;
}
```

위 코드는 f\(n\) = 5n이지만 n이 무한대일때 상수 5가 있다고 해도 달라질게 없으므로 무시해도 된다.

**합의 법칙**

시간 복잡도를 더할 수 있다.

```javascript
function a(n) {
  var count = 0;
  for (var i = 0; i < n; i++) {
    count += 1;
  }
  for (var i = 0; i < 5 * n; i++) {
    count += 1;
  }
  return count;
}
```

결과값은 f\(n\) = 1n + 5n 이며 계수 법칙을 적용하면 시간 복잡도는 O\(n\) 이다.

**곱의 법**

중첩 루프에 곱을 적용한다.

```javascript
function a(n) {
  var count = 0;
  for (var i = 0; i < n; i++) {
    count += 1;
    for (var i = 0; i < 5 * n; i++) {
      count += 1;
    }
  }
  return count;
}
```

결과값은 f\(n\) = 1n \* 5n = 5n² 이며 계수 법칙을 적용하면 시간 복잡도는 O\(n²\) 이다.

**다항 법칙**

시간 복잡도가 다항식일 경우 다항 차수를 적용한다.

```javascript
function a(n) {
  var count = 0;
  for (var i = 0; i < n * n; i++) {
    count += 1;
  }
  return count;
}
```

결과값은 f\(n\) = n² 이며 시간 복잡도는 O\(n²\) 이다.

