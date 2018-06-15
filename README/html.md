# HTML5&CSS3

* [클리어 보스 HTML5 명세](http://html5.clearboth.org/spec)
* [HTML 오픈 레퍼런스](http://html5ref.clearboth.org/)
* [MDN HTML](https://developer.mozilla.org/ko/docs/Web/HTML)
* [MDN CSS](https://developer.mozilla.org/ko/docs/Web/CSS)

# WRIA-ARIA

- 참고자료 링크
  [「예제로 살펴보는 WAI-ARIA」 사례집 제작발표.pdf](https://goo.gl/AAv3jv)

## 등장 배경

최신 웹접근성 지침서 : 한국형 웹컨텐츠 제작 지침 2.1

	웹 콘텐츠 접근성 가이드 라인”의 버전이 업데이트 되면서 신기술을 고려한 형태로 발전되었으나 아직도 ... 부족하다
* RIA의 동적인 웹 애플리케이션 접근성 보장을 위한 지침이 부족
* Ajax를 통한 실시간 변경 콘텐츠를 못 읽을 수 있음
* 페이지 콘텐츠 중 일부만 변경 시, 동일한 내용을 계속 읽어야 하는 문제 발생
* 화면 확대 사용자의 경우, 가시 범위 밖의 콘텐츠 변경 내용을 알 수 없음.

## 목적

마크업에 역할(Role), 속성(Property), 상태(State) 정보를 추가하여 스크린 리더 및 보조 기기 등에서 접근성 및 상호 운용성을 향상시키고 보다 나은 사용자 경험(User Experience)을 제공하기 위함

## 지원현황

http://caniuse.com/#search=wai-aria
IE8+ 지원 가능

## ARIA 세가지 기능

*   역할
    *   특정 요소(Element)에 역할을 정의하는 것
    *   역할을 부여하여 사용자에게 정보를 제공
    *   부여된 역할은 동적으로 변경할 수 없음

```html
<!-- 메뉴 정의 role="menu" -->
<div id="auth_error" role="alertdialog" ...>
  
<!-- 경고 대화상자 정의 role="alertdialog" -->
<div id="auth_error" role="alertdialog" ...>
  
<!-- 버튼 정의 role="button" -->
<div class="btn_01" role="button" ...>
```

* 속성 (Properties) & 상태 (States)

  요소(Element)가 기본적으로 갖고 있는 특징이나 상황

  속성과 상태는 aria-* 접두어를 가진다.

  상태는 요소의 상황을 나타내므로 애플리케이션이 실행 중에 자주 바뀌는 반면, 속성은 상대적으로 바뀌는 경우가 드물다.


  * 속성

    ```html
    <!-- 필수 항목 속성 aria-required -->
    <input type="checkbox" aria‐required="true">

    <!-- 추가 설명 속성 aria-describedby-->
    <input type="text" aria-describedby="reference">
    <div id="reference">추가설명</div>

    <!-- 그룹 제목 속성 aria-label-->
    <div role="group" aria-label="그룹제목">
    ```

  * 상태

    ```html
    <!-- 확장되어 있는 상태의 탭패널 aria-expanded="true" -->
    <div role="tabpanel" aria-expanded="true">

    <!-- 오류가 발생한 상태의 입력상자 aria-invalid="true" -->
    <input type="text" aria-invalid="true">

    <!-- 선택된 상태의 토글버튼 aria-pressed="true" -->
    <button aria-pressed="true">
    ```

## ARIA의 사용

* ARIA 와 HTML5 : ARIA 역할(role)과 HTML5 섹션 요소를 중복해서 사용하지 않는다.

  ```html
  <!-- 잘못된 사용의 예 -->
  <nav role="navigation">
  ```

* HTML 요소의 기능 변경 제한

  ```html
  <h1 role="button">버튼</h1>
  ```

* 키보드 사용 보장

  ```html
  <span role="button" tabindex="0">버튼</span>
  ```

* 레이블 제공

  ```html
  <div>
  	<div id="user‐name">이름</div>
  	<input type="text" id="name" aria-labelledby="user-name">	</div>

  <label for="usr-pwd">비밀번호</label>
  <input type="password" id="usr-pwd" name="usr‐pwd" aria-describedby="message">
  <span id="message" class="guide”>6~12자 이내로 영문, 숫자를 혼합하여 사용</span>
  ```

* table

  xHTML 에 있던  summary 속성이 HTML5 에서 없어짐

  이를 대체하는 방법

  ```html
  <p id="tblDesc">Column one has the location and size of accommodation, other columns show the type and number of properties available.</p>
  <table aria-describedby="tblDesc">
  ...
  </table>
  ```
