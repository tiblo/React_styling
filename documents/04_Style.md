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

리액트의 ``className``은 HTML에서 class와 같다.

```html
<div class="App">

</div>
```
위와 같이 처리된다.

# SASS(SCSS)
Syntactically Awesome Style Sheets.

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
Scss는 Sass에서 지원하는 확장자 형식으로 두 가지는 동일한 전처리기이지만 작성 문법이 조금 다르다.

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
