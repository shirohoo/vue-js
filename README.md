# Vue.js, Vue-CLI

- Reactivity
- Instance
- Component
- Component Communication
    - props
    - event-emit
- Axios - HTTP Library
- Template syntax
    - data-binding
    - vue-directive
- Vue-CLI
- Single file component

---

## 😎 Reactivity

`Vue.js`가 추구하는 핵심 가치이다.

`Vue.js`의 대부분의 기능이 이 가치를 위해 존재한다고 해도 과언이 아니다.

데이터를 바인딩하고, 데이터의 변화를 감지하면 화면에 즉시 반영하는 기법을 말한다.

---

## 😎 Instance

`Vue.js`를 사용하기 위해서는 `Vue` 인스턴스가 반드시 필요하며, 생성자를 사용한다.

이 인스턴스에는 여러가지 메서드가 정의되어 있다.

```javascript
new Vue({
  el        : '#app',
  data      : {},
  components: {},
  mounted   : {},
  computed  : {},
  methods   : {},
  ...
});
```

---

## 😎 Component

`컴포넌트(Component)`는 모던 프론트 프레임워크의 트렌드이다.

HTML을 컴포넌트 단위로 작성하여 재사용성을 키워 최대한 경제적으로 화면을 구성하는 것이다.

이때 `전역 컴포넌트(Global Component)`와 `지역 컴포넌트(Local Component)`로 나뉘며

`전역 컴포넌트`는 말 그대로 `scope`가 `global`인 컴포넌트를 말하며,

`지역 컴포넌트`는 각 컴포넌트의 `Vue 인스턴스`의 `components 블록`에 정의된 컴포넌트를 말한다.

`지역 컴포넌트`는 지역 컴포넌트가 정의된 컴포넌트에서만 `생명주기`를 갖는다.

일반적으로 오픈소스 라이브러리가 `전역 컴포넌트`의 형태로 되어있고,

이를 실제 개발자가 작성하는 경우는 드물며 `지역 컴포넌트`를 아주 많이 사용하게 된다.

```javascript
// 전역 컴포넌트
Vue.component('app-header', {
  template: '<h1>Header Component</h1>'
});

// 지역 컴포넌트
let appHeader = {
  template: '<h1>Header Component</h1>'
}

new Vue({
  components: {
    'app-header': appHeader
  }
})
```

---

## 😎 Component Communication

![image](https://user-images.githubusercontent.com/71188307/120896133-2204de00-c65b-11eb-9905-e7e3494d3cb5.png)


`Component Communication`은 데이터의 흐름을 조금이라도 더 쉽게 파악하기 위한 구조이다.

기본적인 구조는 하기와 같다

상위 컴포넌트에서 하위 컴포넌트로는 `props(data)`가 내려가며,

하위 컴포넌트에서 상위 컴포넌트로는 `event($emit)`가 올라간다

--- 

## 😎 Axios - HTTP Library

`Axios`는 `Vue.js`의 공식적인 HTTP Library이다.

`promise`기반으로 동작하며, `CDN`방식을 이용하여 라이브러리를 사용하거나 `NPM`으로 직접 설치하는 방법으로 나뉜다.

```javascript
// CDN 방식
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script>
  new Vue({
   el: '#app',
   methods: {
     fetch: function() {
          axios.get('https://jsonplaceholder.typicode.com/users/')
               .then(function(response) {
                 console.log(response); // then: 통신 성공시 실행 될 블록
               })
               .catch(function(error) {
                 console.log(error); // catch: 통신 실패시 실행 될 블록
               });
        }
    }
  })
</script>
```

```javascript
// NPM 방식
cd {vue-project-path}

npm i axios
```

```javascript
import axios from 'axios';
new Vue({
  el: '#app',
  methods: {
    fetch: function() {
      axios.get('https://jsonplaceholder.typicode.com/users/')
           .then(function(response) {
             console.log(response); // then: 통신 성공시 실행 될 블록
           })
           .catch(function(error) {
             console.log(error); // catch: 통신 실패시 실행 될 블록
           });
    }
  }
})
```

---

## 😎 Template syntax

`data-binding`은 `Vue 인스턴스`의 데이터와 `HTML`을 동기화시키는 작업이다.

아래의 코드를 보면 `Vue 인스턴스`와 `<div id='app'>` 가 연결돼있고, 

`Vue 인스턴스`의 `data` - `message`가 `{{ message }}` 라는 문법으로 바인딩이 되어있다.

이 상태에서 `message`의 값이 변경되면 `HTML`에 실시간으로 변경된 값이 표시되게 된다.

```javascript
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="utf-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Title<</title>
  </head>
  <body>
    <div id="app">
      {{ message }}
    </div>

    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
      new Vue({
      el        : '#app',
      data      : {
      message: 'hello'
    },
    });
    </script>
  </body>
</html>
```

<br/>

`vue-directive`은 `v-`로 시작하는 `Vue.js`의 문법을 총칭한다.

예를 들자면 `v-on`, `v-if-else`, `v-bind`,`v-model`,`v-show` 등을 말하며,

위의 `data-binding`과 결합하여 강력한 `Reactivity`를 보여준다.

--- 

## 😎 Vue-CLI

`CLI`는 `Command-line interface`의 약자다.

`Vue.js`를 `NPM`과 `Webpack`을 사용하여 명령줄 한두줄만으로 쉽게 사용할 수 있게 해주는 고급기술이다.

프로젝트를 자동으로 생성해주지만, 프로젝트의 구조가 정형화돼있으므로 이에 대한 학습이 필요하다.

프로젝트를 생성하기 위해서는 `Node.js`와 `NPM`이 설치돼있어야 하며

작성자는 아래와 같은 버전을 사용했다.

```text
npm -v
6.14.13

node -v
v14.17.0

vue --version
@vue/cli 4.5.13
```
 
`Node.js`와 `NPM`이 설치돼있다면 `Vue-CLI`를 설치하기 위해 아래의 명령어를 입력한다.

`-g`는 `OS`에 `Vue-CLI`를 전역으로 설치하겠다는 의미이다.

```text
npm install -g @vue/cli
```

이후 `Vue.js` 프로젝트를 생성하기 위한 명령어는 하기와 같다.

```text
cd {project를 생성할 위치}

vue create {project-name}
```

프로젝트가 생성되면 터미널에 적혀있는 대로 

```text
cd {project-name}

npm run serve
```

를 순차적으로 입력하면 `Vue.js` 서버가 뜬다.

생성되는 프로젝트의 구조는 하기와 같다.

```text
Project
├─ README.md
├─ .gitignore
├─ babel.config.js
├─ package.json
├─ package-lock.json
├─ public
│  ├─ favicon.ico
│  └─ index.html
└─ src
   ├─ App.vue
   ├─ main.js
   ├─ components
   └─ assets
      └─ logo.png
```

--- 

## 😎 Single file component

`Vue-CLI`를 이용하여 만든 프로젝트에는 `.vue`확장자를 가진 파일들이 있다.

이를 `싱글파일 컴포넌트(Single file component)`라 부르며, 

이 `싱글파일 컴포넌트`들을 `Webpack`이 잘 엮어내어 사용자들에게 화면을 보여주는 것이다.

공부를 더 해봐야 겠지만 `Webpack`은 `Gradle`과 비슷한 역할을 한다고 생각되며

`바벨(babel)`이라고 부르는 것은 `javascript`가 실행되는 다양한 환경에서

각 시스템들의 호환성을 보장해주기 위한 `indirection`으로

`Java`의 `JVM`과 비슷한 역할을 한다고 이해가 됐다.
