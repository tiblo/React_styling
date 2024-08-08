# Components Styling
컴포넌트 스타일링이란 HTML에서 엘리먼트를 CSS로 스타일을 적용하는 것처럼 리액트의 컴포넌트로 생성될 엘리먼트에 스타일을 적용하는 것이다.

스타일링의 방식은 다음과 같다.
- 일반적인 CSS 방식
- CSS 전처리기 방식
- CSS-In-JS 방식

## 일반적인 CSS 방식
HTML에서 사용하는 CSS를 그대로 적용하는 방식이다. 주로 HTML의 class 속성을 사용하며, 외부 CSS파일에 스타일을 작성하여 리액트 js에서 불러와서 사용한다.

```javascript
import './App.css';

function App() {
  return (
    <div className="App">
	
    </div>
  );
}
```
App.css 파일은 리액트 프로젝트를 생성하면 함께 생성된다.

```css
.App {
  text-align: center;
}
```

리액트의 ``className``은 HTML에서 class와 같다.

```html
<div class="App">

</div>
```
위와 같이 처리된다.

CSS를 활용할 때는 일반적인 front-end 프로젝트처럼 모든 스타일을 하나의 CSS 파일이나 몇 개의 파일로 분할하여 작성하는 방법을 활용한다.

하지만 리액트의 경우 컴포넌트별로 따로 작성하는 경우가 많다. 각 컴포넌트별로 적용할 스타일을 따로 작성함으써 class 명이 중복되는 상황을 피할 수 있으며, 이 후 유지보수나 리뉴얼 시에 해당 부분만을 처리할 수 있는 점, 또 컴포넌트를 재활용하는 등의 유리한 장점을 얻을 수 있기 때문이다.

전체적으로 통일성있는 사이트 디자인을 위한 공통의 CSS를 작성하고 개별적인 컴포넌트를 위한 스타일링을 따로 하는 방식이 주된 방식이다.

## Inline Styling
컴포넌트에 개별적인 Inline styling을 적용할 수 있다. 이때 css property들은 js 객체 형식으로 ``style`` 속성에 작성한다.
```javascript
const MyComponent = () => {
	return (
		<div style={{color: "red", backgroundColor: "black"}}>BOX</div>
	);
}
```

또는 스타일을 작성한 변수를 활용할 수 있다.
```javascript
const MyComponent = () => {
	const divStyle = {color: "red", backgroundColor: "black"};

	return (
		<div style={divStyle}>BOX</div>
	);
}
```

Css property를 작성할 때는 kebab case를 camel case로 변환하면 된다.(font-size -> fontSize)

# SASS(SCSS)
Syntactically Awesome Style Sheets.(문법적으로 멋진 스타일시트)

단순히 반복되는 내용을 줄이고 효율적으로 사용할 수 있도록 만든 CSS 전처리기 스타일시트 언어

## CSS 전처리기(Preprocessor)
변수와 제어용 문장, 내장함수 등이 제공되어 문법에 따라 작성한 문장이 CSS로 만들어지는 방식

종류
- Sass(Scss)
- Less
- Stylus

![image](https://github.com/tiblo/React_edu/assets/34559256/c8ccdf97-3be4-493f-955e-4d32e348ce3e)

(이미지 출처 : https://nykim.work/97)

### Sass vs. Scss
Scss는 Sass에서 지원하는 확장자 형식으로 두 가지는 동일한 전처리기(같은 라이브러리)이지만 작성 문법이 조금 다르다.

.sass
```css
body
	background: yellow
	color: blue
```

.scss
```css
body {
	background: yellow;
	color: blue;
}
```
(예제 출처 : 리액트를 다루는 기술[개정판])

위의 예제에서 보듯 scss가 css와 유사한 구조를 가지고 있기 때문에 일반 css의 경험이 있다면 조금 더 쓰기가 편하다.

.sass 확장자는 중괄호({})와 세미콜론(;)을 사용하지 않고 작성하는 형식이다.

여기에서는 css와 유사한 scss를 사용한다.

## Sass 설치
Scss를 사용한 하려면 scss로 작성한 내용을 css로 변환하기 위한 ``node-sass``라는 라이브러리가 필요하다.

```
> yarn add node-sass
```

## 문법
Scss 문서를 작성하는 기본적인 문법은 일반 css(selector와 properties)와 동일하다. 

### 변수
Scss는 변수의 사용을 지원한다. 반복적으로 사용하는 값들(색상, 글꼴, 간격, 크기 등)을 변수에 저장하여 사용할 수 있다.

변수를 정의할 때는 ``$`` 기호를 사용한다.

```css
$main-color: #0000ff;
$sub-color: #00ffff;
$m-size: 100;
```
``$`` ``변수명`` ``:`` ``설정값`` ``;`` 순으로 작성한다.

변수를 사용할 때도 ``$`` 기호를 사용한다.
```css
body {
	background-color: $main-color;
	width: #{$m-size}px;
	height: #{$m-size}%;
}
```
수치값을 저장하거나 파일명과 같은 변화되는 값을 저장한 변수를 사용할 때 ``#{}``를 활용할 수 있다.
``m-size`` 값은 ``width``에서는 100px로 사용되고, ``height``에서는 100%로 사용된다.


### 중첩
계층화 되어 있는 요소에 스타일을 적용할 때 활용하는 문법으로, 부모 요소의 스타일 영역에 자식 요소의 스타일을 정의하는 방식이다.

```html
<div class="grand-parent">
	<div class="parent">
		<div class="child"></div>
	</div>
</div>
```
Html의 구조가 위와 같을 때 css로 스타일을 작성하면 다음과 같다.
```css
.grand-parent {
	background: red;
}
.grand-parent>.parent {
	background: green;
}
.grand-parent>.parent>.child {
	background: blue;
}
```

Scss의 중첩을 사용하면 다음과 같이 작성할 수 있다.
```css
.grand-parent {
	background: red;

	.parent {
		background: green;

		.child {
			background: blue;
		}
	}
}
```
요소의 계층 구조에 맞춰 스타일을 작성하여 직관적으로 파악할 수 있게 된다. 또한 클래스명을 중복해서 작성하지 않아도 되는 편의성이 제공된다.

### 부모 선택자 참조
``&`` 선택자는 중첩 상태일 때 상위 선택자를 대체하는 기호이다. 

```html
<div class="content-grand-parent">
	<div class="content-parent">
		<div class="content-child"></div>
	</div>
</div>
```
위와 같이 클래스명이 지정되어 있을 경우 다음과 같이 ``&``를 사용하여 작성할 수 있다.
```css
.content {
	&-grand-parent {	/* .content-grand-parent 가 된다. */
		background: red;
	
		&-parent {
			background: green;
	
			&-child {
				background: blue;
			}
		}
	}
}
```
``&``는 가상 선택자를 활용한 스타일 작성에도 활용한다.
```css
.box-div {
	background-color: blue;

	&:hover {
		background-color: gray;
	}
}
```
그 외에도 다중 클래스 활용, 같은 스타일을 사용하는 요소와 요소 사이의 스타일 등에서도 활용한다.
```css
.box-div {
	background-color: blue;
	color: white;
	width: 500px;
	height: 50px;
 
	&.w-10 {
		width: 10%;
	}
	
	& + & {
		margin-top: 50px;
	}
};
```
``+`` 컴포넌트와 컴포너트 사이를 나타낸다. ``& + &``는 같은 선택자를 사용하는 컴포넌트 사이에 적용될 스타일을 설정하는 것을 나타낸다.

두 번째 ``&`` 대신 다른 컴포넌트의 선택자가 올 수 있으며, 예를 들어 ``& + p``이면 ``.box-div``와 ``<p>`` 컴포넌트가 연속적으로 작성되어 있을 때 스타일이 적용된다.

```javascript
const MyComponent = () => {
	return (
		<div>
			<div className="box-div">BOX1</div>
			<div className="box-div w-10">BOX2</div>
			<div className="box-div">BOX3</div>
			<div className="other">BOX4</div>
		</div>
	);
}
```
위 코드에서 ``BOX2`` div는 가로길이가 10%로 표현되며, class가 ``box-div``인 ``div``들 간 사이에 margin-top이 50px씩 적용된다.(``BOX3``과 ``BOX4`` 사이에는 margin-top이 적용되지 않는다.

![image](https://github.com/user-attachments/assets/ae5f2d13-f8c5-47d1-9da7-b8d41815d874)


### Mixin
Scss에서는 ``@mixin``을 사용하여 함수와 같은 형태의 스타일 블록을 정의하여 사용할 수 있다.







