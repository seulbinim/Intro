# Sass(Syntactically Awesome Style Sheets)

## 1. 프리 프로세서(Pre Processor)
Sass는 CSS 전처리기로 .css 파일 중간에 위치하는 하나의 계층이다.  
웹 브라우저는 프로세서로서 웹데이터를 다운로드 받아 해석하여 화면에 해석된 데이터를 렌더링한다.  
Sass등 CSS 확장언어를 활용할 경우 웹브라우저에서 해석되기 전에 CSS로 변경되는 과정이 필요한다.  
이를 브라우저에서 해석되기 전에 프로세싱한다고 해서 프리프로세싱한다고 부른다.

## 2. Sass 설치

### 2-1. JavaScript 개발 환경 구성
Node.js는 Back-End 개발 환경이지만, 오늘 날 Front-End 개발 환경 구축을 위해서 필수적으로 사용된다.  
Node.js의 버전은 6.5.0 이상이면 어떤 것이든 상관 없다. Node.js의 표준 패키지 관리자 NPM(Node Packages Manager)은  
Node.js에 포함되어 있기 때문에 별도로 설치할 필요가 없다.

* Node.js : Google V8 엔진을 사용하여 제작된 JavaScript 런타임
* NPM : Node.js 패키지 매니저
* NVM 사용하여 Node.js 설치/관리 (★★★★★)

#### 2-1-1. NPM 설치 및 확인

```
$ npm install node-sass # 프로젝트 로컬 설치
$ npm install node-sass --global # 컴퓨터 전역 설치
```

- `npm —version` 혹은 축약어로,  `npm -v` 명령어를 입력하여 npm이 잘 설치 되었는지 확인할 수 있다.
- `npm install -g npm@latest` 최신버전으로 업데이트 해주는 명령어로, 여기서 -g는 ‘—-global’의 약자.
- `npm install —-global` 어느위치에서나 노드사스를 설치할 수 있도록 해주는 명령어.
- `npm ls -g` 내가 설치한 노드사스가 잘 되었는지 확인 할 수 있는 명령어.
- `npm show node-sass versions` 노드사스의 버전을 쭉 출력해준다.
- `npm show node-sass@4.* version` 4버전으로 시작하는 노드사스들을 출력.
- `node-sass -—help` 참고 할수있는 옵션들을 보여준다.



## 3. CLI을 이용한 CSS 컴파일링

```css
# 적용전
html {
  font-size: 10px;
  }
body {
  font-size: 1.4rem;
  color: #000;
  background: #fff;
  }

  body *,
  body*::before,
  body *::after {
    content: '';
    box-sizing: border-box;
  }
```

### 3-1. expanded  
코드를 선택자마다 여러 줄로 출력

```
# 입력예시
node-sass lecture.scss lecture.css --output-style expanded
```


```css
# 결과
html {
  font-size: 10px;
}

body {
  font-size: 1.4rem;
  color: #000;
  background: #fff;
}

body *,
body*::before,
body *::after {
  content: '';
  box-sizing: border-box;
}
```

### 3-2. compressed  
코드를 모두 압축하여 출력(사람이 볼게 아냐..)

```
# 입력예시
node-sass lecture.scss lecture.css --output-style compressed
```

```css
# 결과
html{font-size:10px}body{font-size:1.4rem;color:#000;background:#fff}body *,body*::before,body *::after{content:'';box-sizing:border-box}
```

### 3-3. compact
코드를 선택자마다 한 줄로 출력
```
# 입력예시
node-sass lecture.scss lecture.css --output-style compact
```


```css
# 결과
html { font-size: 10px; }

body { font-size: 1.4rem; color: #000; background: #fff; }

body *, body*::before, body *::after { content: ''; box-sizing: border-box; }
```

### 3-4. nested
코드를 선택자마다 여러 줄로 출력하되, 선언 구문의 끝이 마지막 속성 뒤에 위치(기본 값)
```
# 입력예시
node-sass lecture.scss lecture.css --output-style nested
```


```css
# 결과
html {
  font-size: 10px; }

body {
  font-size: 1.4rem;
  color: #000;
  background: #fff; }

body *,
body*::before,
body *::after {
  content: '';
  box-sizing: border-box; }
  ```

## 4. Sass 문법

### 4-1. SCSS

```sass
# 예시
# 변수를 선언하여 연산할수 있다.

$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```


### 4-2. Sass
```sass
# 예시
# 변수를 선언하여 연산할수 있다.
# 들여쓰기 문법을 사용한다.(세미콜론과 중괄호를 사용하지 않는다.)

$font-stack:    Helvetica, sans-serif
$primary-color: #333

body
  font: 100% $font-stack
  color: $primary-color
```

## 5. CSS Sourcemap
CSS SourceMap을 구성하는게 중요하다. 하나의 CSS 파일에 모두 넣는게 아니라,  
공통된 부분을 분리하여 모듈로 관리해야 한다.

### 5-1. Sourcemap 설정 방법 (크롬 브라우져 이용하기)

* CSS SourceMap을 구성하는게 중요하다. 하나의 CSS 파일에 모두 때려 넣는게 아니라,  
공통된 부분을 분리하여 모듈로 관리할 때 유용하다.

* 크롬브라우저는 기본적으로 Sass의 소스맵을 제공하기 때문에, 다음과 같이 세팅해주면 좋다.

#### 크롬 실험 기능 설정 하기

1. 크롬에서 `chrome://flags/` 을 주소창에 입력하고, 개발자 도구 실험 항목을 찾아,  
 `사용`으로 설정을 켜준다.
2. 개발자도구 창 켜기 : 오른쪽마우스 클릭 후 검사버튼 누르거나,  
 `F12`버튼 누르거나, 맥의 경우는 `command + option + i`로 개발자도구를 열 수 있다.
3. 닫기창 옆에있는 햄버거메뉴를 누르면 나오는 `Setting`버튼을 누르거나, `f1`버튼을 누르면  
 Preference 창이 나오는데, 탭을 `Experiments`로 바꾸어서, 다음과 같은 접근성 항목과,  
  LIVE SASS 항목 등 에 체크해준다. `Accessibility`, `Inspection`, `Allow custom UI themes`, `Live SASS`