# CLI(Command Line Interface)

## CLI 명령어
### 1. 현재 작업중인 폴더 확인
`pwd` : print working directory의 줄임말  
현재 작업중인 폴더의 절대경로가 출력 됨. 

### 2. 폴더 생성  
`mkdir` : Make Directory의 줄임말

문법 : `$ mkdir {디렉토리 이름}`
* `~/Desktop $mkdir www`  
`Desktop` 위치에서 `www`라는 이름을 가진 폴더 생성
* `~/Desktop/www $mkdir css js`  
`Desktop`의 `www`폴더 안에 `css` 와 `js` 폴더를 생성

### 3. 디렉토리 이동  
`cd` : change Directory의 줄임말  

문법 : `$ cd {디렉토리 경로}`  
* `cd ./`    - 현재 디렉토리 (생략 가능)  
* `cd ../`   - 상위경로로 한번 올라감  
* `cd ../../` - 상위경로로 2번 올라감  
* `cd ~/Desktop`  - 데스크탑 디렉토리로 바로 이동    

### 4. 디렉토리 및 파일 목록 출력  
`ls` : List Segments의 줄임말

문법 : `$ls {디렉토리 경로}{옵션}`  
* ~/Desktop/www $ls  
:`Desktop` 폴더 내 `www` 폴더의 하위 `목록`을 출력
* ~/Desktop/www $ls -l
:`Desktop` 폴더 내 `www` 폴더의 `목록`을 출력할 때 사용 권한, 소유자, 그룹, 크기, 날짜 등 상세 정보를 함께 표시
* ~/Desktop/www $ls -a
:`Desktop` 폴더 내 `www` 폴더의 숨겨진 `목록`을 포함하여 모든 목록 출력
* ~/Desktop/www $ls -al
:`Desktop` 폴더 내 `www` 폴더의 숨겨진 `목록`을 포함하여 모든 목록을 출력할 때 사용 권한, 소유자, 그룹, 크기, 날짜 등 상세 정보를 함께 표시  

### 5. 파일 생성  
`touch` : 빈 파일을 생성할 경우  
`echo` : 간단한 내용이 들어있는 파일을 생성할 경우

* `~/Desktop/www $touch index.html`  
:`Desktop`의 `www`폴더 안에 `index.html`파일 생성
* `~/Desktop/www $touch js/app.js`
:`Desktop`의 `www`의 `js`폴더안에 `app.js`파일을 생성
* `~/Desktop $echo 'var course = "FDS" ; ' > js/basic.js`    
:`Desktop`에서 `js`폴더안에 `var course = "FDS" ;`내용이 들어간 파일 생성

### 6. 파일 내용 확인하기
`cat` : 파일 내용을 확인하기

문법 :  
`$ cat app.html` : app.html 파일의 내용을 화면에 출력  
`$ cat app.html web.html` : app.html 파일의 내용으로 web.html 파일 내용 덮어쓰기

### 7. 파일/(비어있지 않은)디렉토리 삭제  
`rm` : Remove 줄임말
문법 :  
`$ rm {제거할 파일/디렉토리 이름}`  
`$ rm -r js` : js폴더 내부 하위 디렉토리까지 모두 제거  
`$ rm -rf www` : `www`폴더 안의 하위 디렉토리까지 모두 제거하되, 경고를 나타내지 않음  

### 8. 디렉토리 제거
`rmdir` : Remove Directory 줄임말

문법 :  
`$ rmdir {제거할 디렉토리 이름}`
* `~/Desktop/www $rmdir js`  
:`Desktop`의 `www`폴더 안에 있는 `js`제거  

### 9. 파일/디렉토리 이동 및 이름 변경  
`mv` : Move의 줄임말(이미 존재하는 파일/디렉토리의 경우 이름 변경이 가능)

문법 : 
* `~/Desktop $mv coffee.js js/coffee.js`  
:`Desktop`의 `coffee.js` 파일을 `js`폴더 안으로 이동함
* `~/Desktop $mv coffee.js milk.js`
:`Desktop`의 `coffee.js` 파일명을 `milk.js`로 변경

### 10. 파일/디렉토리 복사  
`cp` : Copy의 줄임말  

문법 : 
* `~/Desktop $cp coffee.js tea.js`  
:`Desktop`의 `coffee.js` 파일을 같은 디렉토리 내에 복사한 후 파일명을 `tea.js`로 변경
* `~/Desktop $cp tea.js js/milk.js`
:`Desktop`의 `tea.js` 파일을 하위 디렉토리인 `js`로 복사한 후 파일명을 `milk.js`로 변경  

### 11. `&&` 명령어 사용  
`명령어 사이에 &&을 넣으면 차례대로 실행`
문법 : `$ mkdir {디렉토리 이름} && cd {디렉토리 이름}`
* `~/Desktop $ mkdir images && cd images`  
: `Desktop`위치에 `images`폴더를 만들고 `images` 폴더로 이동함

## VIM
`vim` 입력 후, 뒤에 바로 원하는 파일의 경로를 적어주면 텍스트 편집기와 같은 창이 보여진다.

```
vim index.html
```
예를들어, 이렇게 입력하면 index.html 파일의 내용을 직접 입력하거나 수정할 수 있는 창이 보여진다.  
내용을 바로 입력하는것은 불가능하고, `i`키를 눌러서 insert 가능하게 한 후, 원하는 내용을 입력하거나 수정할 수 있다.  
입력이 다 끝난 후에는, `esc`키를 누르고 `:wq`를 입력해야 저장을 하고 빠져나올 수 있으며, `:q!`를 입력하면 저장하지 않은 채로 나올 수 있다.

### 1. 커서 이동
  * l 또는 오른쪽 방향키 - 오른쪽 방향으로 이동
  * h 또는 왼쪽 방향키 - 왼쪽 방향으로 이동
  * j 또는 아래쪽 방향키 - 아래쪽 방향으로 이동
  * k 또는 위쪽 방향키  - 위쪽 방향으로 이동
  * 0(zero) - 현재 커서가 있는 줄의 처음으로 이동
  * Shift + $ - 현재 커서가 있는 줄의 마지막으로 이동
  * Shift + G - 파일의 마지막 줄로

### 2. 편집
  * i - 삽입모드
  * u - 실행취소
  * dd - 현재 커서가 있는 줄 삭제
  * 3dd - 현재 커서가 있는 줄부터 아래쪽 방향으로 3줄 삭제
  * dG - 현재 커서가 있는 위치부터 파일의 끝까지 삭제
  * yy - 현재 줄 복사
