# JSX
Javascript Syntax eXtension 또는 JavaScript and Xml의 약자.

React에서 사용하는 비공식 javascript 확장 문법이다.

Jsx로 작성된 element는 Bebel js를 통해 React 문법 및 vanilla js 문법으로 변환되어 처리된다.

React 문법으로 작성된 element는 가독성이 떨어지기 때문에 주로 활용한다.

형태가 HTML과 유사하기 때문에 가독성이 높지만, 완전히 HTML과 동일하지는 않아서 몇가지 유의해야 할 부분이 있다.

## Jsx 문법과 React 문법 비교
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

## Syntax
### 하나의 태그로 작성
Jsx의 여러 element를 반환할 수 없다. 즉, 하나의 element만 작성해야 하며 여러 elements를 작성할 경우 하나의 부모 element로 감싸야 한다.

```javascript
function Component(){
  return (
    <input></input>
    <button><button>
  );
}
```
위와 같이 작성하면 에러가 발생한다. 다음과 같이 작성해야 한다.

```javascript
function Component(){
  return (
    <div>
      <input></input>
      <button><button>
    </div>
  );
}
```

``<div>``와 같은 특정 태그를 사용하고 싶지 않을 경우 ``<>`` ``</>``를 사용할 수 있다.(``<Fragment>`` ``</Fragment>``도 사용)
```javascript
function Component(){
  return (
    <>
      <input></input>
      <button><button>
    </>
  );
}
```

### 종료태그 사용
Jsx는 반드시 시작태그와 종료태그 쌍으로 element를 작성해야 한다. 

예를 들어 html의 ``<input>``태그는 종료태그를 사용하지 않는 태그지만, ``</input>``이 붙어야 한다.
```javascript
function Component(){
  return (
    <div>
      <input type="text" name="data1"></input>
    </div>
  );
}
```

또는 self close할 수도 있음.(주로 사용되는 형태)
```javascript
function Component(){
  return (
    <div>
      <input type="text" name="data1" />
    </div>
  );
}
```

### JavaScript 표현식 활용
return문 위쪽에 작성한 javascript 변수나 함수, 연산식은 ``{`` ``}``로 감싸서 활용할 수 있다.
```javascript
function Component() {
  const n = "홍길동";

  return (
    <>
      <h1>{n}</h1>
    </>
  );
}
```

### 조건 연산자(``(condition)? A : B``)
Jsx 내에서는 if, switch 구문을 사용할 수 없다. 대신에 조건 연산자를 사용하여 분기를 처리한다.
```javascript
function Component() {
  const score = 90;

  return (
    <>
      {score >= 60 ? <p>합격!</p> : <p>불합격!</p>}
    </>
  );
}
```

### 반복
Jsx 내에서는 loop(for, while) 구문을 사용할 수 없다. 대신 map 함수를 사용하여 반복을 처리한다.
```javascript
function Component() {
  const menus = ["아메리카노","카페라떼","카페모카","에스프레소"];

  return (
    <>
      {menus.map(menu => (<il>{menu}</li>))}
    </>
  );
}
```

### className
Jsx에서는 element의 class 속성을 사용할 때 className을 사용한다. className은 HTML로 변환되면 class로 처리된다.
```javascript
function Component() {
  return (
    <>
      <div className="contents">...</div>
    </>
  );
}
```

### Style Properties
Jsx내에서의 css는 Object 형태로 작성되기 때문에 kebab case로 작성할 수 없다. 

``background-color``와 같은 property는 ``backgroundColor``와 같은 camel case로 작성하여야 한다.

```javascript
function Component() {
	const style = {
		backgroundColor: 'red',
		color: 'white'
	}
	return (
    <>
		  <div style={style}>Box</div>
    </>
	);
}
```

