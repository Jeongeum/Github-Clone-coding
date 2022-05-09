# 반응형 - small 브라우저
> small 브라우저 에서는 다음과 같은 사항을 변경한다.

- summary 글자크기 조정
- titles 1개로 보이게 수정
- map 좌우여백 사라지게 수정
- pricing cell을 수직으로 바뀌게 수정
- footer 수직으로 바뀌게 수정

---------------

## summary 수정

눈에 띄는 차이를 보려면 medium 브라우저에서 visual 부분 summary 글자 크기를 보면 된다.

![image](https://user-images.githubusercontent.com/77143425/145684230-2bde6d80-2a11-4a5d-b589-092c6f89cb7a.png)

브라우저 크기가 더 줄어들었을 때는 summary 글자 크기도 줄어든다.

![image](https://user-images.githubusercontent.com/77143425/145684249-a9173b84-3995-48a2-be70-f79e7dc8b024.png)

그래서 summary의 title/description 부분의 글자 크기를 줄이려고 미디어쿼리에서 정의했더니

![image](https://user-images.githubusercontent.com/77143425/145684274-113d5e61-c500-4d13-be15-b9a695cfdd5b.png)

small 미디어쿼리의 우선순위 명시도 점수가 main.css에서보다 낮아서 덮어써지지가 않음.

근데 이 경우는 small 브라우저가 되었을 때 모든 summary의 글자 크기가 줄어들어야 하기 때문에

common (공통 css) 라고 표시한 후 정의하고 !important 를 붙여서 small 디바이스일 때에만 가장 중요한 개념이 되도록 한다.

![image](https://user-images.githubusercontent.com/77143425/145684400-41df1e7e-dcf1-449c-9054-07cb0f354e21.png)

잘 바뀌었다!

-------------

## titles 개수 수정

medium 브라우저에서 했던 것 처럼 width: 50% 를 100%로 바꿔주면 된다! 초간단!!

![image](https://user-images.githubusercontent.com/77143425/145684444-e7822c5b-f659-4e29-a3e6-95edbedfd800.png)


------------

## 지도 좌우 여백 수정

map의 경우 medium 디바이스 미디어쿼리 만들 때 좌우 paddimg 값을 20을 줬었다.

근데 지금 small 에서는 여백을 없애야 하니까 padding 값 줬던 걸 다시 늘린다! 

![image](https://user-images.githubusercontent.com/77143425/145684473-e21b7eec-4f8f-4884-a131-cc56b4556d21.png)

그럼 이렇게 꽉 차는 것을 볼 수 있다.

------------------

## pricing cell 수정

![image](https://user-images.githubusercontent.com/77143425/145684487-63f4bef5-5a6f-4048-a060-4bad4e91ead3.png)

원래 이렇게 서로 수평을 이루었던 cell 부분을 수직으로 바꿔준다.

![image](https://user-images.githubusercontent.com/77143425/145684507-e761efe6-864b-4124-9c24-ac8735fa55b3.png)

display: block 으로 만들고 중간에 border 넣어주면 끝이다!

-----------------

## footer 수정

![image](https://user-images.githubusercontent.com/77143425/145684584-0f7a201a-4b93-4095-8a64-cf345cfe41c4.png)

footer의 경우 원래 float를 통해 양쪽으로 찢어져 있던 형태였다.

![image](https://user-images.githubusercontent.com/77143425/145684542-f59d64d1-1b9c-4d2b-aaed-508158e3e2d8.png)

이게 small 디바이스 크기만큼 줄어들면 이렇게 이상해지는데 float를 없애서 중앙정렬 해줘야 한다. 

![image](https://user-images.githubusercontent.com/77143425/145684625-048aa029-6499-44a2-a120-829769311944.png)

```css
/* FOOTER */
footer .site-links {
    float: none;
}
```

그리고 두 site links는 flex이기 때문에 justify-content로 정렬해준다.

![image](https://user-images.githubusercontent.com/77143425/145684648-9833501b-fe67-45f1-bed5-a93eb81a0943.png)

된줄 알았지만 극단적으로 크기를 확 줄였더니 

![image](https://user-images.githubusercontent.com/77143425/145684672-a20c45c2-ad24-48a5-8a53-ce50191a5675.png)

완전 이상하게 나온다. 고쳐보자!

flex를 block으로 바꿔주고 tex-align으로 가운데 정렬 우선 해준다.

```css
/* FOOTER */
footer .site-links {
    float: none;
    display: block;
    text-align: center;
}
```

![image](https://user-images.githubusercontent.com/77143425/145684706-8ffdc47f-61ba-43c1-8096-5dfa2695fe51.png)

근데 이러면 block 인것 때문에 li태그들이 수직으로 쌓이니까 li태그만 inline으로 바꿔준다.

```css
footer .site-links li {
    display: inline;
}
```

![image](https://user-images.githubusercontent.com/77143425/145684716-8fcbbe6d-c14c-4e02-8a8c-0ddd89f983ce.png)


--------------

## small (모바일 브라우저) 버전 반응형 완료

![스몰 디바이스 완료](https://user-images.githubusercontent.com/77143425/145684741-1006b603-c213-45ee-a431-64c6dd3eaef9.gif)

------------------

# 추가 (중요)

처음 시작할 때에는 main.css 의 가장 하단에서 @media를 써서 구현했었는데 

css 코드가 한두줄도 아니고 몇백줄이라 위아래 왔다갔다 하면서 보기가 정말 불편하다.

이럴 때에는 다음과 같이 브라우저 크기 별 미디어쿼리 css를 만들어준다.

![image](https://user-images.githubusercontent.com/77143425/145684816-a86b792e-d754-4452-90ae-1507a5c4ec7b.png)

그 후 저 css를 html과 연결시켜야 하니까 link태그를 걸어준다. 단, 미디어쿼리를 사용하고 있음을 꼭 명시한다.

```html
<link rel="stylesheet" media="(max-width: 1024px)" href="./css/main_medium.css">
<link rel="stylesheet" media="(max-width: 768px)" href="./css/main_small.css">
```

그러고나서 그냥 평소 css 작성하듯 써주면 된다!