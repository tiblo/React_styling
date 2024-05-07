# SASS(SCSS)
Syntactically Awesome Style Sheets.

단순히 반복되는 내용을 줄이고 효율적으로 사용할 수 있도록 만든 CSS 전처리기 스타일시트 언어

## CSS 전처리기(Preprocessor)
변수와 제어용 문장, 내장함수 등이 제공되어 문법에 따라 작성한 문장이 CSS로 만들어지는 방식

종류
- Sass(Scss)
- Less
- Stylus

![image](https://github.com/tiblo/React_edu/assets/34559256/c0264c83-a2f9-40f3-a809-4d0496658e1c)

(이미지 출처 : https://nykim.work/97)

### Sass vs. Scss
Scss는 Sass에서 지원하는 확장자 형식으로 두 가지는 동일한 전처리기이지만 작성 문법이 조금 다르다.

.sass
```css
$font-stack: Helvetica, sans-serif
$primary-color: #333
 
body
  font: 100% $font-stack
  color: $primary-color
```

.scss
```css
$font-stack: Helvetica, sans-serif;
$primary-color: #333;
 
body {
  font: 100% $font-stack;
  color: $primary-color;
}
```
(예제 출처 : 리액트를 다루는 기술[개정판])

위의 예제에서 보듯 scss가 css와 유사한 구조를 가지고 있기 때문에 일반 css의 경험이 있다면 조금 더 쓰기가 편하다.

.sass 확장자는 중괄호({})와 세미콜론(;)을 사용하지 않고 작성하는 형식이다.
