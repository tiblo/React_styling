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
