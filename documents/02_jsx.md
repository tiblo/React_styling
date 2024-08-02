# JSX
Javascript Syntax eXtension 또는 JavaScript and Xml의 약자.

React에서 사용하는 비공식 javascript 확장 문법이다.

Jsx로 작성된 element는 Bebel js를 통해 React 문법 및 vanilla js 문법으로 변환되어 처리된다.

React 문법으로 작성된 element는 가독성이 떨어지기 때문에 주로 활용한다.

형태가 HTML과 유사하기 때문에 가독성이 높지만, 완전히 HTML과 동일하지는 않아서 몇가지 유의해야 할 부분이 있다.

JSX는 결국 return 문 안에서 HTML 요소를 출력하기 위한 용도로 사용하는 문법이다.

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

return 문에 작성한 html은 일반적으로 ``(``와 ``)``로 묶어서 작성한다. 다만, 하나의 html 요소를 작성하는 경우에는 생략할 수 있으며(주로 생략한다) 2개 이상의 요소(태그)를 작성하는 경우에는 사용해야 한다.

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

JSX 문법(즉, return문 안)에서 ``{``, ``}``로 감싸진 부분은 자바스크립트 코드를 사용하는 부분이다.

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

### 조건부 렌더링
특정 조건에 따라서 요소를 렌더링하기 위해서 ``&&``(AND) 연산자를 사용할 수 있다.
```javascript
function Component() {
  //const item = null;
  const item = "출력할 내용";

  return (
    <>
      {item != null && <p>{item}</p>}
    </>
  );
}
```
``item``이 null이면 아무것도 출력되지 않지만, 뭔가 값이 있으면 해당 내용을 담은 ``<p>`` 요소가 출력된다.

비슷한 경우로 출력할 내용이 ``undefined``인 경우에 대한 처리는 다음과 같이 할 수 있다.
```javascript
function Component() {
  //const name = undefined;
  const name = "userId";

  return <div>{name || 'Guest'}</div>;
}
```
``name``이 ``undefined``인 경우 ``Guest``가 출력되며, ``name``에 값이 들어가 있으면 해당 값이 출력된다.

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
Jsx에서는 element의 ``class`` 속성을 사용할 때 ``className``을 사용한다. ``className``은 HTML로 변환되면 ``class``로 처리된다.

``className``은 react의 문법으로, 자바스크립트에서 ``class``가 예약어이기 때문에 충돌을 피하기 위해 react에서 변경한 것이다.

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
위의 예제는 다음과 같이 작성할 수도 있다.
```javascript
function Component() {
  return (
    <>
      <div style={{
        backgroundColor: 'red',
        color: 'white'
      }}>Box</div>
    </>
  );
}
```
style의 첫 번째 ``{``는 안의 내용이 자바스크립트 문장임을 나타내는 것이며, 두 번째 ``{``는 CSS 속성들을 자바스크립트 객체로 표현하기 위한 것이다.

### 주석
Jsx 내에서 ``{/*…*/}`` 와 같은 형식을 사용.
```javascript
function Component() {
  return (
    <>
      {/* 이건 주석입니다. */}
      <div>Box</div>
    </>
  );
}
```
주석 또한 자바스크립트의 문법이기 때문에 ``{``와 ``}``를 앞뒤에 붙이는 것이다.

### 이벤트 처리
Jsx 문법에서 각 요소의 이벤트 처리 관련 코드를 작성하는 방법은 다음과 같다.

```javascript
function Component() {
  function eventFunc() {
    alert("클릭함!");
  }

  return (
    <div>
      <button onClick={eventFunc}>click</button>
    </div>
  );
}
```
``onClick`` 속성에 함수명을 넣을 때 ``()``를 붙이지 않는다.

``onClick`` 속성에 ``eventFunc()``를 넣게 되면 return이 처리될 때 함수가 호출되는 상황이 만들어 진다.

즉, ``()``를 붙이게 되면 버튼이 클릭될 때 함수가 호출되는게 아니라 버튼이 화면에 그려질 때(렌더링 될 때) 함수가 호출되어 실행되고, 클릭할 때는 실행되지 않는다.

따라서, 버튼이 화면에 그려질 때는 함수가 실행되지 않고 클릭할 때 ``eventFunc``함수가 사용될거라는 것을 나타내기 위해 ``()``를 빼고 작성한다.(함수와 버튼을 연결만 한다는 의미라고 보면 됨)

위의 예제는 화살표 함수를 사용하여 다음과 같이 작성할 수 있다.

```javascript
function Component() {
  const eventFunc = () => alert("클릭함!");
  
  return (
    <div>
      <button onClick={eventFunc}>click</button>
    </div>
  );
}
```
또는 더 간단하게 다음과 같이 작성할 수 있다.
```javascript
function Component() {
  return (
    <div>
      <button onClick={() => alert("클릭함!")}>click</button>
    </div>
  );
}
```




