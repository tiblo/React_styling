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
