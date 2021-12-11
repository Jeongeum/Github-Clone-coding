# 반응형 홈페이지 만들기

## 미디어 쿼리

: 뷰 포트 사이즈가 일정 크기 이하로 줄어들면 다음과 같이 헤더가 변한다.

![image](https://user-images.githubusercontent.com/77143425/145591309-d989d2b7-bddd-451b-b0c8-318b295ef258.png)

메뉴가 사라지고 검색 input 과 버튼도 사라진다.  헤더 뿐만 아니라 visual 부분의 구조도 변한다.

좌/우로 구분되어있던 레이아웃 구조가 가운데 정렬이 되는 형식으로 변경되었다.

오른쪽 상단의 햄버거 버튼을 누르면 숨어있던 메뉴들이 나타나게 된다.

![image](https://user-images.githubusercontent.com/77143425/145593100-55a7877c-c027-4549-864d-ca5c5460cbab.png)

타일즈부분도 한 줄에 2개로 줄어들었고 

![image](https://user-images.githubusercontent.com/77143425/145593178-83425f88-c7c1-4b82-aeaf-9989b552ca41.png)

푸터 부분도 로고가 사라졌다.

이렇게 뷰포트 사이즈에 맞춰 배치되는게 **반응형**이고 반응형 홈페이지를 만들기 위해서는 미디어쿼리를 알아야 한다.

-----------------

미디어 쿼리는 특정 뷰포트의 크기일 때 이 구조를 어떻게 바꿀지 설정하는 것이다.

**@media** : 원하는 사이즈일 때 구조가 어떻게 변경되는지 설정 가능하다.

```css
@media 미디어타입 and (미디어특성) {
css 코드
}
```
예를 들어보면 

```css
@media screen and (max-width: 1200px) { 
body {
color: red;
}
}
```
우리가 보는 화면의 최대 가로 너비가 1200 일때까지 body 태그의 글자 색상을 red로 한다.

이런 뜻이다 !

### 미디어 타입
타입 | 의미 | 기본값
--|:--:|--:
'all' |  모든 미디어 타입 | 'all'
'screen' | 컴퓨터 화면, 태블릿, 휴대폰 등 | 
'print' | 인쇄 전용 |

### 미디어 특성
 - max-width : 최대 가로너비 **이하**에서 적용
 - min-width : 최소 가로너비 **이상**에서 적용
 - orientation : 뷰포트의 영향을 받음 (portrait , landscape)

![image](https://user-images.githubusercontent.com/77143425/145679332-9a1c2137-49fb-4361-b777-95e227715814.png)

### Media(Grid) options
>디바이스 종류에 따른 단위는 '기획 / 디자인' 단계에서 결정하는 것이 효과적이다.

종류 | 디바이스 | 단위(px)
-- | -- | --
Large Devices | Desktops | 1024px 이상
Medium Devices | Tablets | 1024px 이하
Small Devices | Tablets + Phones | 768px 이하


코드펜 실습)

1. max-width 가 700px 일 때 -> width가 700px을 넘지 않을 때 해당 스타일 적용

![반응형1](https://user-images.githubusercontent.com/77143425/145683683-78fe4048-097a-4695-962c-ee4c6d2d3b52.gif)

2. orientation 이 landscape일 때에는 뷰포트의 가로 너비 > 세로너비 일 경우를 말한다.

![image](https://user-images.githubusercontent.com/77143425/145683797-d538c605-12c1-434d-80d8-5f79f13a9de6.png)

뷰포트의 가로가 세로보다 길기 때문에 landscape 를 만족하고 blue가 된다.

![반응형2](https://user-images.githubusercontent.com/77143425/145683731-28552e66-2583-40c0-a371-8d027c1ccff2.gif)

3. orientation 이 portrait 일 때에는 뷰포트의 세로너비 > 가로너비 일 경우를 말한다.

![image](https://user-images.githubusercontent.com/77143425/145679455-80201807-0a1a-41ee-8cfd-1dd9e429d6ef.png)

--------------

## header 반응형 변경 파악

![image](https://user-images.githubusercontent.com/77143425/145679529-242cb3af-e11e-4caf-94d4-7d4efdff2f06.png)

1. 헤더부분의 이너가 왼쪽 끝부터 오른쪽 끝까지 붙어있다. 이너의 가로 너비를 초기화 해야 한다.
2. 헤더의 세로 너비도 화면이 줄어들면서 같이 줄어든다.
3. 토글 버튼을 누르면 헤더가 **늘어나면서** 기존의 메뉴들이 나타난다.

## header - mideum 크기일 때 토글버튼1

헤더의 이너 크기를 초기화 해줘야 하는데 max-width가 정의될 곳은 section의 inner 이고 덮어쓰려해도 덮어써지지 않는다.

section inner 는 클래스 선택자가 2개여서 10점+10점 = 20점의 명시도 점수를 가지고 있으며

내가 작성한 header inner는 태그 선택자+클래스 선택자라서 1점+11점 = 12점이라 데스크탑의 속성(20점)을 11점으로는 덮어쓸 수 없다.

그래서 덮어쓰려면 header inner가 아니라 section inner 로 해야 하는데 그러면 홈페이지의 모든 inner가 다 초기화 된다.

이럴 때에는 !

![image](https://user-images.githubusercontent.com/77143425/145679590-3a26085d-f3e7-4d6f-b3c1-4e2bd6d7cd4d.png)

header.section .inner라고 써서 **헤더이면서 section 클래스를 가진 요소의 inner라는 max-width가 none이다.** 이렇게 해야만 한다.

그리고 높이도 그냥 줄이면 되겠다고 생각할 수 있지만 그렇지 않다!

토글 버튼을 누르면 메뉴가 주루룩 나와야 하는데 height를 몇 px 이라고 픽스시켜버리면 메뉴가 늘어나면서 수직으로 보여질 수가 없다.

그래서 height: auto 라고 설정해야 한다!

그러고 나서 헤더를 보면 토글버튼을 눌렀을 때 수직으로 쌓이니까 처음에 왼/오로 분할해준 것 처럼 따로 분할을 할 필요가 없어진다. 

그럼 float도 초기화 되어야 맞다.

그 후 메뉴부분을 보면 왼쪽의 로고와 토글버튼 뿐이다. 
![image](https://user-images.githubusercontent.com/77143425/145679865-42c5a8ea-8062-4883-93c5-1706e17de0c7.png)

그리고 토글버튼을 누르면 메뉴가 주루룩 나와야 한다.

![image](https://user-images.githubusercontent.com/77143425/145679916-bb803813-f84f-498d-9c49-4fb29eb8a444.png)

그러기 위해서는 이 메뉴들이 없다가 -> 토글버튼 누르면 나오게 되어야 한다. 

즉, main-menu와 sign-menu를 사라지게끔 해줘야 하는데 이는 toggle class를 주면 된다.

![image](https://user-images.githubusercontent.com/77143425/145680280-87141923-4d9f-4b5e-b091-13bc74a7316a.png)

sign-group 밑에 토글버튼 div를 만들고 대체 텍스트를 작성한 후 잠깐 main.css를 정의한다.

![image](https://user-images.githubusercontent.com/77143425/145680318-d1f031f1-38a1-4ff9-baa5-ab0d0bb0ffb8.png)

대체 텍스트가 안보이게끔 텍스트를 -9999px만큼 밀어주고 position: absolute 를 주는데  

부모 요소인 section .inner에 relative가 있기 때문에 미디어쿼리의 헤더 이너부분에서 position을 안적어줘도 된다.

다시 미디어쿼리로 돌아와서 로고에 padding 을 줘서 

![image](https://user-images.githubusercontent.com/77143425/145680449-46ab197a-fc48-4d03-8572-88821b95f8ad.png)

이렇게 토글이 제대로 보이지 않는 것을 해결해 준다.

![image](https://user-images.githubusercontent.com/77143425/145680456-dcea4612-215f-4e01-a25f-6a91deb2c2cd.png)

짠 잘나타난다!

---------------

## header - 토글버튼 2

![image](https://user-images.githubusercontent.com/77143425/145680524-e15310f9-5b96-4a40-9b6e-ee250b089fce.png)

수평으로 되어있는 메뉴를 1024px 이하에서 

![image](https://user-images.githubusercontent.com/77143425/145680513-b7cbefd9-4f4c-409f-912f-89f5efe90ab1.png)

수직으로 나타나게 바꿔보자!

우선, main-menu (로고있는 왼쪽 메뉴부분) 먼저 해볼건데 

기존에는 main-menu가 flex였기 때문에 메뉴들이 수평으로 나타날 수 있었기 때문에 이번에는 block으로 바꿔준다.

근데 그렇게 하고 나면 약간 모양이 이상해진다.

![image](https://user-images.githubusercontent.com/77143425/145680578-519c5bde-4394-44a3-94c9-15049bd7d745.png)

이렇게 로고의 옆으로 메인 메뉴가 쌓이게 된다. 

이건 메뉴그룹 (로고와 왼쪽메뉴 합친 부분) 에서 로고와 왼쪽 메뉴를 수평 만들려고 flex 줘서 그렇다.

이것도 block으로 바꿔주면 

![image](https://user-images.githubusercontent.com/77143425/145680620-117969c5-cf9c-4921-8c2f-d6bafb76e362.png)

로고 밑으로 메인메뉴가 수직으로 쌓인다. 이제 여기에는 정렬 잘 시켜주고 선 넣어주고 하면 된다.

![image](https://user-images.githubusercontent.com/77143425/145680646-fbbec5de-0528-488f-9621-ee3951a41311.png)

짠!

방금 메인메뉴 한 것 처럼 사인메뉴도 수평을 위해 flex 준 것을 block으로 바꿔주면 된다.

근데 사인메뉴의 경우 수평으로 보일때와 수직으로 보일때 순서가 달랐었는데 

이건 애초에 html 구조 잡을 때 거꾸로 써주고 order로 자리 잡아줬으니 지금은 건드릴 필요 없다!

여기에서는 그냥 메뉴에서 버튼과 input이 작은 크기이니까 메뉴 전체적으로 쓰게끔 바꿔줘야 한다.

근데 수평인 두 버튼을 수직으로 바꿔주려고 block을 적용했더니 수직이 되질 않는다.

이유를 찾아보니까 기존에 미리 정의하고 가져다 쓰는 btn css에서 display를 inline-flex로 해놔서 그렇다. 

그냥 flex로 바꾸고 다시 미디어 쿼리에서 block으로 바꾼다.

![image](https://user-images.githubusercontent.com/77143425/145680765-5ab3f0bc-1dfe-46a3-a37d-b378e59b08d1.png)

수직이 됨과 동시에 너비 전체를 쓴다!

input의 경우는 전체 너비를 쓰기 위해서 px로 정의된 너비를 미디어쿼리에서는 100%로 바꿔준다.

서브 메뉴들은 margin을 주고 flex니까 justify-content로 가운데 정렬 해준다.

![image](https://user-images.githubusercontent.com/77143425/145680865-9777d9c5-ba52-42a8-a37d-d2a6e72b984a.png)

-------------------

## 토글버튼2 - js 작성하기

토글버튼을 눌러야 헤더가 내려오면서 메뉴가 보이게끔 해야하는데 이 행위는 어떠한 **액션을** 통해 내용이 나타나고 사라져야 한다.

클릭을 했을 때 나타나고 사라지는 작업을 **event** 라 하고 이걸 js로 해야 한다.

나는 toggle-btn을 클릭했을 때 on 클래스가 추가/제거 되도록 하려고 한다.

main.js를 생성하고 
```js
(function (window, document) {
    'use strict';
...
})(window, document)
```

이런식으로 작성을 할건데 아직 js를 안배워서 자세히는 모르지만 이해한 바로는 다음과 같다.

전체 영역에서 윈도우 객체와 도큐먼트 객체를 즉시 실행함수가 인수로 받게 되고 그 인수를 함수의 인수로 전달한다.

함수 안의 내용이 전체 영역을 더럽힐 수 있기 때문에 부분화(모듈화)해주는 것이다.

use strict는 엄격한 js 문법을 통해 코드를 작성하겠다고 선언하는 것이다.

![image](https://user-images.githubusercontent.com/77143425/145682524-0333dd89-0338-43da-9696-3afbbd4bb814.png)

4줄 : toggle 클래스를 가진 요소를 불러온다.
5줄 : toggle-btn 아이디를 가진 요소를 불러온다.
7줄 함수 : 클릭 이벤트를 리스너 메소드를 통해 감지하고 toggleElements() 함수를 실행한다.
11줄 함수 : toggles는 유사배열인데 유사배열을 불러와서 반복시킨다. 
- 반복 시키는 이유 : toggle 클래스가 2개 있다는 것을 알고 있는데 나중에는 혹시나 여러개가 될 수도 있음. 

갯수가 유동적으로 변할 수 있기 때문에 toggle 클래스를 가진 요소들을 싹 찾아서 그 요소들을 하나씩 정리함.

17줄 함수 : toggle 클래스를 가진 요소에 on이라는 클래스를 지속적으로 toggle(보이고 사라지는것을 반복) 한다.
23줄 함수 : toggle 클래스를 가진 요소에 on이라는 클래스를 제거한다.

js는 

```html
<script defer src="./main.js"></script>
```

이렇게 실행해서 html 전체가 로딩이 끝나면 그때 main.js를 실행하도록 한다.

짠!

![반응형3](https://user-images.githubusercontent.com/77143425/145683902-2e0f2a37-6eed-476b-962c-3d17c0120d9a.gif)

-----------------

이번에는 두가지를 해보자.

1. medium 브라우저 크기에서 토글 버튼을 눌렀을 때 메뉴가 수직으로 뜨고 그 상태에서 화면을 늘리면 대체 텍스트가 뜨는 점.

![image](https://user-images.githubusercontent.com/77143425/145682868-8eadec06-9059-48e4-be44-1c7ae87c6c0f.png)

: 대체 텍스트는 기존 브라우저 상태에서는 안보여야하고 medium 브라우저에서 토글버튼으로 나타나야하기 때문에

![image](https://user-images.githubusercontent.com/77143425/145683031-215db8d2-b85e-4529-ba3a-ff535efe75f3.png)

main.css 정의 시 display: none으로 하고 미디어쿼리에서는 1024 이하일 때 display: block으로 한다.

이때, 미디어쿼리쪽에서 버튼을 생성하지말고 애초에 main.css에서 토글버튼을 만들어두고 안보이게만 하는게 좋다!

 
2. 토글 버튼을 눌렀다가 그 상태에서 화면 늘린 후 다시 줄이면 메뉴가 안보여야 하는데 보이는 점.

: main.js의 11줄에서 **resize** 추가한다.

![image](https://user-images.githubusercontent.com/77143425/145683096-8d400896-46a0-4db5-b107-b5e9f9503bcc.png)

윈도우는 브라우저를 의미하고 브라우저에 resize라는 이벤트가 발생할 때 특정함수를 실행한다~ 라고 해석되게끔 한다.

여기서의 이벤트는 브라우저 사이즈가 1024px 이상이 되었다가 줄어들었다가 하는 것이다.

브라우저 너비가 1024 이상이면 on 클래스를 끄게끔 해준다.

![image](https://user-images.githubusercontent.com/77143425/145683192-ef9848fb-93b9-4e03-8b4b-31ff59098de7.png)

토클버튼이 없다가 브라우저 크기가 줄어들면

![image](https://user-images.githubusercontent.com/77143425/145683202-02da5a07-e39e-441a-a0d5-9e6885ad9c27.png)

생긴다!

------------------

## visual 영역 

visual 영역은 크기가 줄어들면 수평에서 수직으로 바뀌고 중앙정렬된다.

![image](https://user-images.githubusercontent.com/77143425/145683210-ceb2bf80-71f5-4d6e-b55b-c18ee5b09020.png)

![image](https://user-images.githubusercontent.com/77143425/145683934-9e389d2d-58b0-457d-a51f-3bccc084bf05.png)

우선, inner flex를 block으로 바꿔서 수직으로 만들고 summary 부분 text-align: center 를 줘서 중앙정렬 한다.

sign-form의 경우 너비를 auto로 줘서 초기화 시키고 max-width 를 줘서 

500px 이하에서는 브라우저 크기에 맞게 알아서 줄어들고 커지고 하게끔 한다.

![image](https://user-images.githubusercontent.com/77143425/145683300-37eaa152-0fac-45d8-9a00-b5c385f06c2e.png)

이런식으로!

그 후, 뒤에 마스코트가 잘 안보이니까 1024px 이하에서는 작은 브라우저 용 배경화면으로 바꿔준다.

![image](https://user-images.githubusercontent.com/77143425/145683320-96d1745b-a7ce-45b8-b4fb-821dc1acee26.png)

해당 브라우저 크기에 맞는 배경을 visual 부분에 새로 넣으면 이렇게 좀 더 화면에 맞아보인다.

----------------------

## feature 영역

: tiles 부분이 기존 브라우저에서는 4개가 한줄로 보이다가 medium 브라우저에서는 한줄에 2개씩으로 보인다.

이건 매우 간단한데 width 값을 현재 25%로 되어있으니까 50%로 바꾸면 된다.

![image](https://user-images.githubusercontent.com/77143425/145683393-79b4ecdd-2166-4180-abbf-f4c3d8e7f56d.png)

그럼 이렇게 두개씩 뜬다.

두번째 사진 border-right 없애고 이미지 크기 약간 조정, 여백 등을 주면 끝이다.

--------------------

## footer 영역

![image](https://user-images.githubusercontent.com/77143425/145683499-cf1b6314-0319-4f50-ae6e-f1bc5382e19b.png)

이렇게 기존 브라우저에서는 로고가 보였는데

![image](https://user-images.githubusercontent.com/77143425/145683511-cb54fcc6-ff3c-4eb2-b0e7-e4eb257df579.png)

안보이게 바꿔준다!

로고 부분만 display: none 하면된다.

---------------
## medium (태블릿 브라우저) 버전 반응형 완료

![미디움 디바이스 완료](https://user-images.githubusercontent.com/77143425/145683609-934b24a1-cb72-4d88-ad01-442e14e828ea.gif)


