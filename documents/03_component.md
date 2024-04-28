# Component
React는 SPA(Single Page Application) 방식의 View 라이브러리이다.

다양한 화면의 처리를 위해 다수의 HTML 페이지를 작성하는 방식이 아닌 하나의 HTML 페이지에 Contents를 바꾸는 방식으로 동작한다.

이러한 Contents를 컴포넌트(Component)라고 한다.

컴포넌트는 하나의 페이지가 될 수 있으며, ``<button>``이나 ``<div>``와 같은 하나의 element가 될 수도 있다. 즉, 여러 컴포넌트로 하나의 컴포넌트를 구성할 수 있다.

## Class Component vs. Function Component
컴포넌트는 클래스형 컴포넌트와 함수형 컴포넌트로 작성하는 방법이 있다.

### Class Component
클래스형 컴포넌트는 Component class를 상속하여 작성하며, 화면에 출력할 element를 render() 함수에 작성하는 방식이다.

```javascript
import React, { Component } from 'react';
 
class MyComponent extends Component {
  render() {
    const name = '홍길동';
    return <div className="react">{name}</div>;
  }
}
 
export default MyComponent;
```

#### Class Component의 장단점
클래스 내장 변수인 state를 생성하여 활용할 수 있으며, 라이프사이클의 각 단계에 해당하는 기능을 사용할 수 있고 임의 메서드를 정의하여 활용할 수 있다.

