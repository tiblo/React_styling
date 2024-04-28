# JSX
Javascript Syntax eXtension 또는 JavaScript and Xml의 약자.

React에서 사용하는 비공식 javascript 확장 문법이다.

Jsx로 작성된 element는 Bebel js를 통해 React 문법 및 vanilla js 문법으로 변환되어 처리된다.

React 문법으로 작성된 element는 가독성이 떨어지기 때문에 주로 활용한다.

형태가 HTML과 유사하기 때문에 가독성이 높지만, 완전히 HTML과 동일하지는 않아서 몇가지 유의해야 할 부분이 있다.

Jsx의 div element
```javascript
function Component(){
  return (
    <div>Box</div>
  );
}
```

React의 div element
```javascript
function Component(){
  return React.createElement("div", null, "Box");
}
```
