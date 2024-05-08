# Board Project
- Back-end : Spring boot
- Front-end : React

## React Extension Package
- Page 이동 : react-router-dom
- Component 스타일링 : node-sass
- REST 통신용 : axios
- 날짜/시간 형식 지정 : moment
- 다중 Class 명 처리 : classname
- Form 유효성 처리 : react-hook-form
- Fontawsome 아이콘

## React Part
> Project name : board

### 프로젝트 생성
```
yarn create react-app board
```

프로젝트 생성 후 폴더를 ``board``로 변경

프로젝트 실행
```
yarn start
```

### 패키지 추가
다음과 같이 패키지를 추가한다. 순서는 상관없다.
```
yarn add react-router-dom
yarn add node-sass
yarn add axios
yarn add moment
yarn add classname
yarn add react-hook-form
yarn add @fortawesome/fontawesome-svg-core
yarn add @fortawesome/free-solid-svg-icons
yarn add @fortawesome/react-fontawesome@latest
```

#### font awesome 아이콘 사용해 보기(https://fontawesome.com/icons)
종류 : solid, regular, light, thin, duotone, brand
1. 기본(core) 패키지 설치
npm i @fortawesome/fontawesome-svg-core
2. 아이콘 패키지 설치
npm i @fortawesome/free-solid-svg-icons 
npm i @fortawesome/free-regular-svg-icons
...
3. 리액트용 컴포넌트
npm i @fortawesome/react-fontawesome@latest

