## Header

![image](https://user-images.githubusercontent.com/77143425/145147596-48da5e37-3c30-468e-adba-3d720f9ab927.png)

내가 클론 코딩할 github 홈페이지 윗부분을 보면 

하나의 section의 영역 안에서 컨텐츠들을 감싸서 화면의 중앙으로 몰아주는 역할을 하는 요소가 있다.

보통 이런 요소의 이름을 container , wrapper , inner 라고 지정한다.

헤더 부분도 메인 부분도 다 중앙 쪽으로 몰려있고 수직도 맞춰져 있다.

![image](https://user-images.githubusercontent.com/77143425/145149289-bd80dafa-cec2-46c0-a524-fed5f1e28c94.png)

헤더부분을 자세히 보면 inner로 감싼 후 또 크게 left right로 나뉜다.

- left : 로고 이미지와 personal , open source, busibess explore 

- right : pricing , blog , support , input 태그 , sign in , sign up 


:star: 그리고 메뉴에는 되도록이면 목록을 만들어주는 ul, ol, li 태그들을 사용해 주는 것이 좋다.

![image](https://user-images.githubusercontent.com/77143425/145151950-ba1b7f8f-8767-4610-8604-dcb6e3a7a969.png)

![image](https://user-images.githubusercontent.com/77143425/145152033-9ac992d6-e80a-47b6-b16e-637ad41201df.png)

일단 이렇게 작성할 수 있다.

-----------
### 왼쪽 메뉴

max-width를 줘서 최대 980px만큼 커지고 상황에 따라 너비가 줄어들 수도 있게 끔 설정한다.

그리고나서 높이를 주게 되는데 

![image](https://user-images.githubusercontent.com/77143425/145152241-f5a0ab79-4ffe-4fce-a64f-2471f90b0af2.png)

inner에 높이 값을 주는 이유 :question:

만약 header에 높이값을 주게 되면 inner에 또 높이 값을 줘야 한다. 

근데 inner에만 높이값을  주게 되면 

header의 기본 값은 auto 이기 때문에 자식요소인 inner의 영향을 받아 자동으로 높이 값이 맞춰진다.

그다음 inner의 너비 값으로는 최대 980px로 지정한다,

최대 너비 값은 max-width를 사용하면 되고 최대 980px까지 늘어나며 상황에 따라 크기가 줄어들 수도 있다.

자!! 이번에는 inner 라는 영역을 가운데 정렬 해보자.

가운데 정렬을 해줄 수 있는 대표적인 속성은 **margin: 0 auto** 이다.

눈에 띄게 확인해보기 위해 배경색을 빨갛게 하고 확인해보자.

- margin 적용 전
![image](https://user-images.githubusercontent.com/77143425/145152897-224f3ed0-ce09-4abc-bcee-24a01a18c70d.png)

- margin 적용 후
![image](https://user-images.githubusercontent.com/77143425/145152950-e7ef9c39-85f0-47c1-a50a-1ab7cb33aa80.png)

짠! 이렇게 inner 가 가운데 정렬이 되었다.

여기서 주의사항!!

margin : 0 auto 를 사용하기 위해서는 반드시 특정 요소에 가로 사이즈가 정의되어 있어야 한다.

다음으로 menu-group 에 대해 css를 정의할 건데 

현재 inner는 단순히 특정 section (여기서는 header) 안에 있는 모든 컨텐츠들을 특정한 가로 너비를 가지면서 중앙정렬을 위해 만들어져 있기 때문에 

```css
header .inner .menu-group {
  ...  
  }
```

이렇게 매번 입력해 주는것은 연관성도 없고 불편하고 관리가 어렵다.

그렇기 때문에 inner는 지우고 후손선택자를 통해 바로 menu-group으로 갈 수 있게 정의하면 된다.

그 후, menu-group 안에 있는 로고와 메인메뉴가 수평 정렬이 되도록 해야하기 때문에 display: flex 를 적용해준다.

```css
header .menu-group {
    display: flex;
  }
```

![image](https://user-images.githubusercontent.com/77143425/145153767-cf22e689-3a8f-4bf9-8ee5-a9ccc529fe0d.png)

그러면 이렇게 로고와 메인메뉴가 수평 정렬이 된 것을 볼 수 있다.

그리고 각각의 메인 메뉴에 있는 값들이 수평 정렬 되도록 하기 위해 메인메뉴에도 display:flex를 적용한다.

```css
header .main-menu {
    display: flex;
  }
```

![image](https://user-images.githubusercontent.com/77143425/145153862-a3192740-b6b3-43ac-831d-89298e95d0a9.png)

이렇게 각각의 메인메뉴들도 다 수평 정렬이 되었다.


----------

이제는 menu-group 부분의 영역을 확인해보자.

눈에 띄게 확인하기 위해서 background : tomato로 주고 확인해보면

![image](https://user-images.githubusercontent.com/77143425/145154290-f55d220c-3c0a-4519-83e4-ec81f69c1b28.png)

이렇게 영역이 정해져있다.

근데 우리는 깃헙 홈페이지에서 본 것 처럼 

![image](https://user-images.githubusercontent.com/77143425/145154376-b6b1fc83-f3d5-40cd-ae87-9d7efa5ca714.png)

메뉴 안의 각각의 내용들이 수직 가운데 정렬이 되길 원한다.

그러려면 메뉴 그룹의 높이를 헤더 전체 높이만큼 확장해야 한다.

메뉴그룹 에서 수평 정렬을 위해 flex를 사용했었고 flex를 사용하면 쓸 수 있는 수직정렬인 align-items : center을 사용해준다.

그 후, 메뉴그룹의 높이를 지정해주는데 height : 100% 를 준다.

이때 부모 요소인 inner의 영향을 받아 78px 의 100%를 사용하게 된다.

![image](https://user-images.githubusercontent.com/77143425/145154812-223d62c5-7637-49a7-ad3b-708bbeeb4e45.png)

그 후, 로고와 메인메뉴가 너무 붙어있으니까 로고에 margin-right : 10px 만 줘서 약간 공간을 만들어주고

메인 메뉴들끼리도 너무 붙어있으니까 margin-right를 줘보자.

```css
header .logo {
    margin-right: 10px;
  }
```

margin을 주고나서 영역 확인을 위해 배경색을 입히고 확인해봤더니

![image](https://user-images.githubusercontent.com/77143425/145155427-c9aad3cc-8ca7-4b2f-a039-6a2f4a31098d.png)

각각의 메인 메뉴들끼리 공간이 생기긴 했는데 영역이 너무 좁다..!!

이렇게 되면 메뉴를 클릭하려고 할때 꼭 글씨부분만 클릭을 해야해서 약간 불편할 수가 있다.

이럴때에는 margin이 아니라 padding을 주면 안쪽에서 여백이 생기기 때문에 편하다.

```css
header .main-menu li {
    padding: 10px;
    background: tomato;
  }
```

![image](https://user-images.githubusercontent.com/77143425/145155530-a69fa22a-a297-4887-b645-0417d09221e9.png)

padding을 주니까 똑같이 각각의 메뉴들은 여백이 생기면서도 각자의 영역은 넓어졌다.

하지만 그래도 아직까지 글씨만을 입력해야 한다.

:question: 이유가 뭘까 :question:

우리가 지금 padding을 주고 배경색을 준건 li 태그이다. 근데 실제로 눌리고 이동하는건 li 태그 속의 a태그이다.

그래서 우리는 실질적으로 클릭이 가능한 범위를 li 태그 안에 있는 a 태그에게 줘야 한다.

```css
header .main-menu li a {
    padding: 10px;
    background: tomato;
  }
```

![부트스트랩11](https://user-images.githubusercontent.com/77143425/145155942-e71969f8-19ff-464c-9696-e6e1f6c72f31.gif)

여백 부분에 마우스를 가져다 대면 마우스 모양이 바뀐다!

그리고 a 태그는 기본적으로 inline 요소이기 때문에 padding의 위아래 값을 가질 수 없다. 

그렇기 때문에 display를 block으로 바꿔주고 글씨 색상도 주고 배경색도 없앤다.

```css
header .main-menu li a {
    display: block;
    padding: 10px;
    color: #3c4146;
  }
```

![image](https://user-images.githubusercontent.com/77143425/145156342-7c758e30-4820-451b-9136-20cbab80ff34.png)


그리고 마우스를 각각의 메인 메뉴에 올렸을 때 색상이 바뀌도록 한다.

```css
header .main-menu li a:hover {
    color: #4078c0;
  }
```

![부트스트랩13](https://user-images.githubusercontent.com/77143425/145160041-3f424cf8-a0c7-4a2f-a545-d1dc2762679f.gif)

------------------
이번엔 로고 부분에 이미지를 넣어보자.

logo에서 실질적으로 클릭되는 건 a태그이기 때문에 a태그에  background로 이미지를 넣어보도록 한다.

url을 통해 이미지를 넣고 보니 a태그는 inline요소라서 범위를 가질 수가 없고 그렇다보니 이미지를 표현할 수가 없다. 

이미지에 범위를 주기 위해 display:block을 주고 너비/높이를 지정해준다.

```css
header .logo a{
    background: url("../img/logo.svg");
    width: 32px;
    height: 32px;
    display: block;
  }
```

![image](https://user-images.githubusercontent.com/77143425/145157168-94dc1693-e5e3-4a37-859d-256f1c2b8657.png)

로고 이미지가 제대로 나타난다! 근데 a태그 부분에 써줬던 GitHub이라는 글씨와 이미지가 겹쳐 보인다.

만약에 a태그가 아니라 img 태그를 썼다면 필수 속성으로 alt이 있어서 이 이미지가 뭘 뜻하는지 적어줄 수가 있지만 a태그의 경우에는 그런걸 적을 수가 없게 된다.

그렇다고 해서 Github이라는 글자를 지울수도 없다.

이럴때 우리는 예전에 배웠던 들여쓰기를 활용한다.

글씨를 써놨지만 보이지 않게 큰 px을 적용하여 숨기는 것이다,

text-indent : -9999px 을 주어서 글씨를 왼쪽으로 약 10000px 옮겨준다.

![image](https://user-images.githubusercontent.com/77143425/145157445-fb742a42-d31e-469b-aba0-e901fc6ece72.png)

그럼 글씨가 안보여서 마치 안쓴 것 처럼! 하지만 저 로고가 뭔지에 대해서 표현할 수 있다.

(굳이 9999를 쓰는이유 :question: : 만약에 12345px을 쓰면 이게 무슨 의미인지 알 수 없다.
9999px을 써주면 마치 약속한 것처럼 대체 텍스트 기법을 썼구나! 라고 알 수 있다.)

추가로 로고에 마우스를 가져다 댔을 때 로고의 색상을 바꾸게 만들기 위해서 가상클래스 선택자 :hover를 이용해서 별개의 이미지로 교체한다.

```css
header .logo a:hover {
    background: url("../img/logo_on.svg");
  }
```
![부트스트랩12](https://user-images.githubusercontent.com/77143425/145157913-8f34026d-40c6-4a1d-b6b4-994e288d09a9.gif)

----------------------

### 2. 오른쪽 메뉴

오른쪽 메뉴는 우선 GitHub 홈페이지를 보면 다음과 같은 구성이다.

![image](https://user-images.githubusercontent.com/77143425/145160880-c98cae8b-08b1-49c6-8179-24d52bf7bc3c.png)

차례로 서브메뉴 , 입력양식 , 버튼 이렇게 세개인데 

이렇게 순서대로 만들면 되는게 아니냐! 라고 생각할 수도 있지만 (나도 그랬고) 아니다!

홈페이지의 너비를 줄여보면 부트 스트랩에서 배웠던 것처럼 메뉴바가 생기고 

메뉴가 바 안으로 다 숨게 되는데 오른쪽 메뉴 부분의 순서를 잘 보면

![image](https://user-images.githubusercontent.com/77143425/145161650-41db5d6a-e1bd-45ad-9dea-b448ab317a57.png)

순서가 거꾸로다..!!!!

그래서 화면이 클때처럼 만드는게 아니라 일단은 위에서 아래로 쌓이게끔 만들고 

나중에 수평이 되었을 때 순서를 다시 뒤집는 방식으로 할것이다.

- 틀 만들기

```html
<div class="sign-group">
                <div class="btn-group">

                </div>
                <form action="">

                </form>
                <ul class="sub-menu">
                    
                </ul>
            </div>
```

자 이제 먼저 버튼을 만들어 보자.

버튼을 누르면 로그인과 회원가입이 가능한 페이지로 이동해야 하기 때문에 a태그를 사용한다.

미리 만들어둔 버튼에 대한 css가 있으므로 class="btn" 을 써준다.

녹색 버튼의 경우 btn--primary 라는 이름으로 css 를 만들어뒀기 때문에 btn 뒤에 클래스를 더 추가해준다.

![image](https://user-images.githubusercontent.com/77143425/145164203-3a23b0dd-3299-4d57-bd05-f59ab8cb47f8.png)

그러고나서 보면 모든 a태그에 밑줄이 그어져 있는 것을 볼 수 있다. 이는 a태그의 특징? 인데 없애주면 된다!

![image](https://user-images.githubusercontent.com/77143425/145164392-3d1b26dd-9ce4-47fd-864b-eb24989eff22.png)

css의 윗부분에 공통적으로 적용되게끔 common 부분에 적어주면 모든 a태그들의 밑줄이 사라진다.

![image](https://user-images.githubusercontent.com/77143425/145164458-ec373076-33e5-4c32-a13b-20e8553e6d08.png)

밑줄이 사라지고 아주 깔끔해졌다.

아! 그리고 보니까 sign in 버튼 부분의 글자 색이 파란색이다.

이는 일부러 의도한 것은 아니고 a태그의 기본 컬러가 파란색인건데 

sign up 의 경우 btn-primary 버튼을 정의할때 임의로 컬러를 흰색으로 정의해줬지만

기본 버튼모양인 btn은 글자색을 정의하지 않은 것을 확인했다.

그래서 btn 부분에 color: #333을 추가해서 어둡게 만들어준다.

![image](https://user-images.githubusercontent.com/77143425/145164838-ccd92e6b-3f41-4651-bf4c-fc78c364ce18.png)

지금처럼 중간에 문제점이 생기면 보완할 수 있어야 한다. 

form 태그 안에 input 태그도 넣고 서치할 수 있는 버튼인 submit 버튼도 넣어준다. 

그리고 서브메뉴도 ul-li 태그를 통해 넣어준다.

```css
<div class="sign-group">
                <div class="btn-group">
                    <a href="#" class="btn sign-in">Sign in</a>
                    <a href="#" class="btn btn--primary sign-up">Sign up</a>
                </div>
                <form id="search-form" method="post" action="">
                    <input type="text" id="search" class="input--text" placeholder="Search GitHub">
                    <input type="submit" value="submit">
                </form>
                <ul class="sub-menu">
                    <li><a href="#">Pricing</a></li>
                    <li><a href="#">Blog</a></li>
                    <li><a href="#">Support</a></li>
                    
                </ul>
            </div>
```

![image](https://user-images.githubusercontent.com/77143425/145167081-2196e05d-9cd4-49c1-9c0a-c7c5d1650cc7.png)

이제 css로 가서 모양새를 만들어주자.

우선 수직으로 쌓여있는 것을 수평으로 만들어주기 위해 sign-group에 dissplay:flex를 해준다.

![image](https://user-images.githubusercontent.com/77143425/145167569-a188521d-54c2-4b3c-8b87-d946dd838c91.png)

수평이 되었다.

이제 여기에서 줄바꿈 되어있는 메뉴를 헤더의 오른쪽으로 옮겨야 하고 

서브밋 버튼 글자도 안보이게 해주고 li 태그도 수평으로 만들어줘야 한다.

----------

줄바꿈 되어있는 메뉴를 헤더의 오른쪽으로 옮기려면 float에 대한 이해가 필요하다!

![image](https://user-images.githubusercontent.com/77143425/145168662-20d926e6-6c97-4eb1-90c9-f4e67d21f9a3.png)

이렇게 두개의 item div를 만들어서 실습해보자.

div는 기본적으로 block요소이기 때문에 수직으로 쌓이게 된다.

이 item에 float을 적용해보자.

두 아이템을 각각 left, right로 float 적용을 해주었더니 어라...

부모 요소인 컨테이너의 높이가 쪼그라들어버렸다.

이유는 :question:

=> float 을 적용하면 item이 공중으로 뜨기 때문에 부모요소가 제대로 감쌀 수 없는 환경이 되었기 때문이다.

그래서 .cleaarfix라는 클래스를 정의해서 float를 적용한 요소의 **부모요소**에 clearfix를 적용해서 해제를 해야 한다.

![image](https://user-images.githubusercontent.com/77143425/145169294-600a871d-1bcb-425a-aa43-13198270ac2e.png)

clearfix를 정의하고 그 클래스를 컨테이너에도 적용시키면 

위와같이 부모요소에서 float가 양쪽 다 해제되어 제대로 아이템을 감쌀 수 있게 된다.

이 예제를 가지고 실제로 적용을 하면 된다!

그 런 데

매번 왼쪽메뉴엔 float:left를 쓰고 오른쪽 메뉴엔 float:right를 쓰고 ...  부모요소를 찾아서 clearfix 해주고 .. 

이게 매번 하기 너무 불편하니까 공통 클래스를 만들듯이 미리 정의해주고 가져다 쓰면 편해진다.

![image](https://user-images.githubusercontent.com/77143425/145170028-acc2db9e-3142-42f3-8a90-deb5cf52769b.png)

이렇게 정의를 미리 해준다.

그러고 부모요소와 각각의 왼/오른쪽 메뉴에 클래스를 써주면

![image](https://user-images.githubusercontent.com/77143425/145170340-b026b812-f65d-4637-9d7f-2d7b6edd2b3d.png)

이렇게 정렬이 제대로 된다!

이제 순서를 뒤바꿔줘야 하는데 이때 사용할 수 있는 속성은 **order** 이다.

order은 순서가 클 수록 뒤로 밀려나는 속성이라고 배웠다!

그럼 생각해봤을 때, 두개의 버튼이 가장 뒤로 가야하고 , 서브메뉴가 가장 앞으로 와야한다.

```css
header .btn-group {
    order: 2;
  }

  #search-form {
    order: 1;
  }

  .sub-menu {

  }
```

그럴때에는 버튼과 폼 양식만 order를 지정 해주고 서브메뉴는 기본값인 0 그대로 둔다.

![image](https://user-images.githubusercontent.com/77143425/145171828-56ae1509-7ae3-4042-b738-59b8a88b8241.png)

order을 이용해서 순서도 재배치 해주고 기존에 왼쪽 메뉴에서 했던 대로 

오른쪽 서브메뉴 (ul 태그라서 수직으로 쌓인 부분)에도 flex를 주어 수평으로 만들어준다.

```css
 header .sub-menu li a {
    padding: 8px;
    display: block;
    font-size: 13px;
    color: #3c4146
  }

  header .sub-menu li a:hover {
    color: #4078c0;
  }
```
왼쪽 메뉴에서 했던 것 처럼 li 태그 안의 a태그 (실직적으로 클릭되는 부분) 에 padding 값을 주어 다닥다닥 붙은 것을 떼주고

padding 값이 잘 먹도록 하기 위해 block 요소로 변경도 시켜준다.

아무래도 서브메뉴이다보니 글씨 크기도 약간 줄여주고 색상도 바꾼다.

또한, 마우스를 올렸을 때 파란색으로 바뀌게끔 :hover 도 지정한다.

![image](https://user-images.githubusercontent.com/77143425/145172271-c1a39bf8-dfc1-442a-ab57-7545b328404d.png)

좀 모양새를 갖춘 것 같다!!! 

이제 해결해야 할 것은 폼 양식 부분!

input 태그 안에 들어가는 저 글씨가 서브 메뉴인데 넘 크다. 

글씨 크기를 줄여주고 동시에 가로 너비도 약간 조정해준다.

```css
#search {
    width: 160px;
    font-size: 14px;
  }
```


아 이때 id의 경우에는 고유한 값이기 때문에 굳이 앞에 부모 요소 안적어도 된다! 불필요한 요소가 될 뿐!!

그리고 옆에 있는 submit 버튼... 안보이게 해주자 !

근데 서브밋 버튼을 없애려고 하니까 또 class="" 어쩌구~~ 해줘야 한다.

이게 클래스가 자꾸 늘어나다보면 헷갈리고 복잡하다.

그래서 다음 선택자를 이용해서 

```css
#search + [type="submit"] {
    display: none;
  }
```
#search의 다음 선택자인 type이 submit인 요소의 display를 none ! 안보이게 하겠다고 정의해 준다.

![image](https://user-images.githubusercontent.com/77143425/145172874-ef01a719-43fe-49c0-9436-4accc115b5a7.png)

짠!! 서브밋 버튼이 안보인다.

![image](https://user-images.githubusercontent.com/77143425/145174123-83c0d4d7-c16b-4579-ab86-01b8c2e4a987.png)

근데 잘보면 버튼과 버튼 사이에 공간이 있다.

나는 분명 공간을 설정한 적이 없는데... 

이유는 간단하다!

=> 우리가 버튼 모양을 css로 미리 정의할 때 display를 inline-flex로 만들어뒀었다.

인라인 요소는 수평으로 만들어지지만 여백을 가질 수가 없게 되는데 인라인 요소를 두개 이상 만들게 되면

![image](https://user-images.githubusercontent.com/77143425/145174769-86b7b6fd-63a1-4f35-a74f-34c6d21dd5a0.png)

코드 입력 후 줄바꿈했을 때 그 줄바꿈을 한칸 띄어쓰기로 인식을 해버린다.

그래서 저 버튼들도 약간 여백이 생긴 것이다.

그래서 나는 저 버튼들이 있는 btn-group 으로 가서 dlsplay: flex로 설정했다,

![image](https://user-images.githubusercontent.com/77143425/145174981-fbf0ad3b-8d23-4b5a-bf83-d40316e64fc4.png)

여백이 사라진 것을 확인할 수 있고 flex되면서 수평정렬 되었기 때문에 제어하기에도 수월하다.

자 그럼 마무리로 서브메뉴와 폼, 버튼이 너무 다닥다닥 붙어있으니까 그 부분만 여백을 줘보자.

```css
header .btn-group .sign-in {
    margin-right: 4px;
  }

#search-form {
    order: 1;
    margin-right: 12px;
  }

header .sub-menu {
    display: flex;
    margin-right: 10px;
  }
```

알맞는 마진 값을 주고 저장 후 보면

![image](https://user-images.githubusercontent.com/77143425/145175410-82e18463-6c6a-4ac2-9f36-36e4d0c9e8db.png)

여백이 생겨 더 보기 깔끔해졌다.

