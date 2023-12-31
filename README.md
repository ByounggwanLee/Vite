# Vite
### A. 개발환경 구성
#### 1. Node설치
* 터미널을 열고 NodeJs 버전 확인
```
node -v
```
* 버전정보가 나오지 않는다면 아래주소에 접속하여 NodeJs를 설치
> [LYNMP 홈페이지](https://nodejs.org)

#### 2. Vue설치
* Vue버전 확인
```
vue --version
```
* 버전정보가 확인 되지 않으며 vue설치
```
npm install -g vue
```    
* Vue/Cli 설치
> vue-cli는 기본 vue 개발환경을 설정해주는 도구임.
```
npm install -g @vue/cli
```
* vite 설치
> vue-cli는 기본 vue 개발환경을 설정해주는 도구임.
```
npm install -g vite
```
#### 3. Vetur확장프로램 설치
vue파일의 스니펫, 하일라이트, 포맷팅을 해주는 확장프로그램
* Vscode > 확장 프로그램 > vetur 검색(maker : Pine Wu)
![image](https://github.com/ByounggwanLee/Vite/assets/108439363/be6d53ff-13af-478e-a04a-f0542e410d5c)

### B. 프로젝트 생성
npm을 이용하여 Vite 기반의 Vue 프로젝트를 생성한다.
#### 1. cmd(VSCode 터미널)에서 프로젝트를 생성하고 싶은 위치로 이동 후 npm 명령어로 프로젝트 생성
npm init vue@latest 명령어를 입력하고 프로젝트 이름과 옵션을 선택하면 프로젝트가 생성된다.
![image](https://github.com/ByounggwanLee/Vite/assets/108439363/dbe325e1-f574-40cf-9c49-2cebe8ff548a)
> * Router - src/router 폴더가 생성된다.<br>
> * Pinia - src/stores 폴더가 생성된다.<br>
>   * 기존의 Vue 상태 관리 라이브러리인 Vuex를 대체할 수 있는 라이브러리<br>
> * ESLint - .eslintrc.cjs 파일이 생성된다.<br>
> * Prettier - .prettierrc.json 파일이 생성된다.<br>

npm init vite@latest 명령어를 입력하고 프로젝트 이름과 옵션을 선택하면 프로젝트가 생성된다.
![image](https://github.com/ByounggwanLee/Vite/assets/108439363/ea3aa3af-5b90-4446-915c-839dcba9071f)

#### 2. 프로젝트 폴더로 이동하여 npm을 설치한다.
cd <프로젝트 이름>
npm install

npm install을 진행하면 프로젝트에 node_modules 폴더가 생성되고, 필요한 JavaScript library들이 설치된다.

#### 3. VSCode로 프로젝트 열기
* npm install 전 프로젝트 구조<br>
![image](https://github.com/ByounggwanLee/Vite/assets/108439363/ba248583-f105-41ae-a300-7cfce0dd1229)
  * node_modules 폴더가 존재하지 않는다.

![image](https://github.com/ByounggwanLee/Vite/assets/108439363/c76d42cc-1888-4ede-968a-d6f8d0c90f11)   
* npm install 후 프로젝트 구조
  * node_modules 폴더와 package-lock.json 파일이 생성되었다.<br>
![image](https://github.com/ByounggwanLee/Vite/assets/108439363/dfb59c2d-a7a4-4435-8ffa-ae058f651368)
![image](https://github.com/ByounggwanLee/Vite/assets/108439363/6e47f4fc-0343-4e00-93a1-bfd1bd75a191)

### C. 프로젝트 기본 구조

![image](https://github.com/ByounggwanLee/Vite/assets/108439363/3fa1b2b1-7089-4b0e-97d6-56d8066769f8)
![image](https://github.com/ByounggwanLee/Vite/assets/108439363/d0adb07f-7670-4030-9ccc-6ff08587a5ab)

* package.json
  * 프로젝트에 대한 정보
  * 프로젝트의 이름, 버전, private 여부, 배포 및 개발에서 사용할 모듈 정보, 실행 명령어, 지원할 브라우저에 대한 설정 등을 포함
  * dependencies: 배포 환경에서 사용되는 모듈
  * devDependencies: 개발 환경에서 사용되는 모듈
    
* package-lock.json
  * package.json의 모듈들이 동작하기 위해 필요로 하는 모듈들의 정보
  * npm install 과정에서 npm이 package.json의 내용을 확인하고 package-lock.json 파일을 생성한다.
  * package.json이 수정되면 package-lock.json도 수정된다.

* node_modules
  * npm install 과정에서 생성된다.
    * package-lock.json의 모듈들이 설치된다.
        * package.json에 종속된 자바스크립트 라이브러리들

* public
  * component(.vue 파일)에서 사용되지 않는 정적 파일들
  * cf) assets와는 달리 webpack의 처리를 받지 않는다.

* src
  * 작성해야 하는 소스코드들 (대부분의 코딩이 이루어지는 곳)
  * assets
    * component(.vue 파일)에서 사용되는 정적 파일들
    * cf) public과는 달리 webpack의 처리를 받는다.
  * views
    * .vue 확장자를 가진 컴포넌트 파일들 - 화면 전체에 해당하는 컴포넌트를 관리 (cf. components)
  * components
    * .vue 확장자를 가진 컴포넌트 파일들 - 화면 전체가 아니라 부분으로 구성되어 재사용할 수 있는 컴포넌트 (cf. views)
    * \<template>, <script>, <style> 부분으로 나뉜다.
      * \<template>: HTML로 화면상에 표시할 요소들을 작성
      * <script>: 스크립트 코드 작성. import/export
      * <style>: HTML 요소를 꾸며줄 css 구문 작성. scoped 속성을 사용하면 특정 컴포넌트에서만 고유의 스타일 선언 가능 
  * router
    * Routing: 웹 페이지 간의 이동 방법으로 Single Page Application(SPA)에서 주로 사용된다.
      * SPA: 페이지를 이동할 때마다 서버에서 웹 페이지를 요청하여 새로 갱신하는 것이 아니라, 사용할 페이지들을 미리 받아놓고 페이지 이동시에 클라이언트 라우팅을 이용하여 화면을 갱신하는 방법
   * stores
     * Vue의 상태 관리 라이브러리
   * main.js
     * 프로그램 시작 지점(entry point)
   
* .eslintrc.cjs
  * 코드에 대한 eslint 설정
  * Prettier에 대한 값으로 rule 지정
   
* .prettierrc.json
  * Prettier 설정

* vite.config.js
  * Vite에 대한 설정

#### 4. 프로젝트 실행
* package.json
```
{
  "name": "vue-project",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "dev": "vite", // 개발 서버에서 프로젝트를 실행할 때 실행되는 명령어
    "build": "vite build", // 빌드할 때 실행되는 명령어
    "preview": "vite preview", // 개발 환경에서의 미리보기
    "lint": "eslint . --ext .vue,.js,.jsx,.cjs,.mjs --fix --ignore-path .gitignore"
  	 // eslint로 문법 체크
  },
  "dependencies": { // 배포 환경에서 필요한 라이브러리 정보
    "pinia": "^2.0.28",
    "vue": "^3.2.45",
    "vue-router": "^4.1.6"
  },
  "devDependencies": { // 개발 환경에서 필요한 라이브러리 정보
    "@rushstack/eslint-patch": "^1.1.4",
    "@vitejs/plugin-vue": "^4.0.0",
    "@vue/eslint-config-prettier": "^7.0.0",
    "eslint": "^8.22.0",
    "eslint-plugin-vue": "^9.3.0",
    "prettier": "^2.7.1",
    "vite": "^4.0.0"
  }
}
```
* 프로젝트 실행: 터미널 창에 npm run dev 입력
```
D:\Vite\vue-project>npm run dev

> vue-project@0.0.0 dev
> vite


  VITE v5.0.10  ready in 549 ms

  ➜  Local:   http://127.0.0.1:5173/
  ➜  Network: use --host to expose
  ➜  press h + enter to show help
```
* 프로젝트 빌드: 터미널 창에 npm run build 입력
```
D:\Vite\vue-project>npm run build

> vue-project@0.0.0 build
> vite build

vite v5.0.10 building for production...
✓ 44 modules transformed.
dist/index.html                      0.43 kB │ gzip:  0.29 kB
dist/assets/AboutView-ug8e6cRs.css   0.09 kB │ gzip:  0.10 kB
dist/assets/index-x6itbcqJ.css       4.21 kB │ gzip:  1.30 kB
dist/assets/AboutView-FIK4syfU.js    0.22 kB │ gzip:  0.20 kB
dist/assets/index-tBwP6Qjq.js       86.76 kB │ gzip: 34.20 kB
✓ built in 1.02s
```
* 실행 화면
![image](https://github.com/ByounggwanLee/Vite/assets/108439363/2a73bdcc-e8b9-473f-ab6d-1428088f96a0)
