# 반응형 CSS 기초

## 반응형 웹
> 반응형 웹이란, 다양한 기기나 브라우저의 크기에 맞게 구성이나 크기를 변경해가며 반응하는 웹문서 또는 이를 위해 사용하는 기법을 뜻한다.
 
 ### 모바일의 등장
 > 스마트 모바일 기기의 등장으로, 데스크톱 화면을 위해 존재했던 웹문서의 설계에도 변화가 요구되기 시작했고, 변화의 초기에는 모바일 전용 URL을 제공하는 방법이 주로 사용되었다.
 
 예)    
데스크톱 https://www.naver.com/   
모바일 https://m.naver.com/ 

## 뷰포트
> **뷰포트(viewport)란 현재 화면에 보여지고 있는 영역을 의미한다.**   
기기 별로 뷰포트가 다르기 때문에, 동일한 웹 페이지라도 기기에 따른 배율 조정이 발생해 화면의 크기가 다른게 보이는 현상이 나타난다.  

## 절대 길이 단위 px
> 입문 레벨에서 가장 많이 사용하는 단위인 px은 절대 길이 단위이다.   
px은 어떤 상황에서도 동일한 값을 유지하므로, 가변성이 없다.

## em과 rem   

> em과 rem은 박스에서 텍스트 크기를 조정할 떄 사용하는 상대 단위이다.   
**em은 부모 요소의 글꼴 크기를, rem은 루트 요소의 글꼴 크기를 의미한다.** 

- em으로 여백 크기(padding와 margin)을 정할 때는 자기 자신의 글자 크기를 기준으로 한다.
 
```css
<div style="font-size: 20px;">
 <p>자식 요소의 1em은 20px!</p>
 <p>자식 요소의 2em은 40px!</p>
</div>
```
### em과 rem이 반응하지 않는다?
> em과 rem은 주변 상황에 따라 그 크기를 달리할 수  가변성을 지니고 있지만,   
 **브라우저나 기기화면에 크기에 따라 크기라 따라 크기가 달라지는 단위는 아니다 따라서 반응형이라고 할 수는 없다.**

 ### 반응하는 단위들
 - 뷰포트의 크기를 기반으로 값을 계산하여 크기를 결정하는 가변 단위
 ```css
font-size: 1vw; /* 뷰포트 너비의 100분의 1*/
font-size: 1vh; /* 뷰포트 높이 100분의 1*/

font-size: 1vmin; /* 뷰포트 높이와 너비 중 작은 쪽의 100분의 1*/
font-size: 1vmax; /* 뷰포트 높이와 너비 중 큰 쪽의 100분의 1*/
 ```

 ### 비율에 기반한 크기 조절
 > em을 이용해 상대적인 크기의 폰트를 적용할 때처럼, 레이아웃도 비율에 기반한 개념을 적용할 수 있다.   
 부모 요소의 크기에 비례에 자식 요소의 크기가 변하는 방식은 가변 레이아웃을 만들 떼 흔히 사용되는 방식이다.

 그럴 떄 사용되는 상대적이고 비례적인 단위는 바로 **%(퍼센트)** 이다.
 ```css
 % 단위는 백분율 값을 나타낸다. 보통 부모 요소와의 상대적 크기를 지정할 때 사용한다. 
 너비와 높이, 여백 뿐 아니라 글자 크기에도 사용할 수 있다.
 /* 부모 요소의 글자 크기가 100% */
 font-size: 50%;
 /* 부모 요소의 높이가 100% */
 height: 50%;

 /* 부모 요소의 너비가 100%*/
 width: 50%;
 margin: 10%;
 padding: 10%;
 ```
- 너비와 여백은 부모 요소의 너비에 비례해 계산된다.
- 높이는 부모 요소의 높이에 비례해 계산된다.
- 글자 크기는 부모 요소의 글자 크기에 비례해 계산된다.

## CSS 함수란 뭘까?
> 수학에서의 함수와 코딩(프로그래밍)에서의 함수는 비슷한 개념이다.   
함수란 주어진 인수에 따라 정해지는 값을 일컫는 표현으로, CSS의 속성값을 지정할 때도 함수 개념을 적용할 수 있다.

### CSS 함수
> CSS의 함수는 괄호 안에 인수를 전달하면, 인수에 따른 결과값을 속성에 적용하는 방식으로 동작한다. ex) 함수명(x)

#### CSS 함수의 대표 함수, calc()
> CSS 함수 calc()를 이용하면 계산식의 결과를 속성값으로 지정할 수 있다.   
calc() 함수는 괄호안에 표현식 하나를 받고, 표현식의 결과가 최종 값이 된다.   
표현식은 단순 계산식이면 무엇이든 가능하다.   
width: calc(30px - 20px)

## 미디어 쿼리
> 미디어 쿼리(media query)는 미디어 타입을 인식하고, 콘텐츠를 읽어들이는 기기나 브라우저의 물리적 속성을 감지할 수 있는 유용한 장치(기능)   
모든 미디어 쿼리는 다음 두 가지 구성 요소를 지닌다.   

- 미디어 타입
- 조건에 대한 물음(쿼리)

```css
@media 미디어_타입 and (조건에_대한_물음) {
  /*
  미디어 타입과 조건을
  모두 만족할 때 덮어씌울
  스타일 선언문
  */
}

@media screen and (max-width: 768px) {
  /*
  화면의 너비가 786px 이하일 경우에 
  여기에 정의된 스타일 선언문을 추가 적용할 것이다.
  */
}
```
```css
img{
  width: 200px;
  height: 200px;
}

@media screen and (min-width: 800px) {
  img{
    width: 400px;
    height: 400px;
  }
}
@media screen and (min-width: 1200px) {
  img{
    width: 800px;
    height: 800px;
  }
}
```

### 미디어 타입과 쿼리
> 미디어 쿼리에 입력할 수 있는 미디어 타입과 쿼리의 종류는 다양하다.(주로 사용되는 것들은 거의 정해져 있다.)

|속성명|정의|속성명|정의|
|:--:|:--:|:--:|:--:|
|min-width|디스플레이 영역의 최소 너비|orientation|portrait 또는 landscape 감지|
|max-width|디스플레이 영역의 최대 너비|color|기기의 색상당 비트 수|
|min-height|디스플레이 영역의 최소 높이|color-index|출력 기기의 색상 테이블 수|
|max-height|디스플레이 영역의 최대 높이|aspect-ratio|디스플레이 영역의 너비와 높이의 비율|

### 미디어 쿼리 적용의 다른 형태
> 다음과 같은 방식으로도 미디어 쿼리를 적용할 수 있다.
- link 태크에 미디어 쿼리 추가
```css
<link rel = "stylesheet" href="style.css"
media="screen and (max-width: 768px)">
```
- @import 구문을 이용한 추가
```css
@import url("style.css") screen and (max-width: 768px);
```
## picture
> HTML의 picture 요소를 이용하면 뷰포트의 너비 등 브라우저의 특정 조건에 따라 이미지를 반응형으로 불러 올 수 있다.
```html
<picture>
  <source srcset="desktop.png" media="(min-width: 1200px)">
  <source srcset="tablet.png" media="(min-width: 800px)">
  <img src="mobile.png">
</picture>
```

## 가변 video
```html
<video src="./video/video.mp4" controls></video>

<div class="player">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/Jc1MGgTb2sc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen>
  </iframe>
</div>

``` 
```css
.player{
  padding-top: 56.25%; // 315/560
  position: relative;
}

iframe{
  position: absolute;
  top: 0; left: 0;
  width: 100%;
  height: 100%;
}
```

