# React
메타(메타 플랫폼, 페이스북)에서 개발한 오픈 소스 자바스크립트 라이브러리.<br>
SPA(Single Page Application)를 전제로 하는 라이브러리.<br>
기본적으로 모듈형 개발이기 때문에 생산성 또한 상당히 높은 라이브러리라서 현재 대세..(?)<br>
전체 페이지를 분할하여 조합하는 방식. 분할된 조각을 컴포넌트(Component)라고 함.

## 개발환경 설정
### Node.js 설치
https://nodejs.org/en

### Yarn 설치
node 설치 후 VSCode 터미널에서 npm으로 설치
```
npm install -g yarn
```

### 설치 확인
node 확인
```
node -v
```

yarn 확인
```
yarn -v
```

## React Components Styling
React Components Styling 방식
* CSS(기존 방식)
* SCSS
* CSS Module
* Styled-Components
* React Bootstrap

# VScode에서 React 디버깅

https://velog.io/@chori/React-%EA%B0%9C%EB%B0%9C%EC%A4%91-vsCode-%EB%94%94%EB%B2%84%EA%B9%85-%EB%B0%A9%EB%B2%95

디버그 아이콘 클릭 > create a launch.json file 클릭
> .vscode 폴더와 launch.json 파일이 생성됨<br>
  다음과 같이 입력
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "chrome",
            "request": "launch",
            "name": "Launch Chrome against localhost",
            "url": "http://localhost:3000",
            "webRoot": "${workspaceFolder}"
        }
    ]
}
```
터미널에서 먼저 npm start로 서버를 구동해야 함.

# VSCode Extentions
* Auto Rename Tag
* Auto Close Tag
* Reactjs code snippets
  * rsc(React Stateless Component)로 함수형 컴포넌트 자동 생성

# React 프로젝트 복사 및 이동 후
node_modules의 용량이 많기 때문에 제외하고 압축하여 옮기게 된다.

새로운 환경에서 다시 프로젝트를 실행할 경우 다음과 같이 node_modules을 설치해야 한다.
```
> npm install
```
package.json의 내용을 확인하여 필요한 node_modules을 설치한다.

# 터미널에 글자가 깨지는 경우 해결법
![image](https://github.com/tiblo/React_edu/assets/34559256/b0da1558-e0ee-48b0-9c72-cf364cc963e1)

setting.json에 다음을 추가
```
{
    ...
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

안되면(안된다..) 다음 코드를 터미널에서 실행
```
chcp 65001
```

![image](https://github.com/tiblo/React_edu/assets/34559256/70bcf883-99e9-4850-bb55-acb5943073fd)

해결~
