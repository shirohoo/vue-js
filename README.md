# π Vue.js, Vue-CLI

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

## π Reactivity

`Vue.js`κ° μΆκ΅¬νλ ν΅μ¬ κ°μΉμ΄λ€.

`Vue.js`μ λλΆλΆμ κΈ°λ₯μ΄ μ΄ κ°μΉλ₯Ό μν΄ μ‘΄μ¬νλ€κ³  ν΄λ κ³ΌμΈμ΄ μλλ€.

λ°μ΄ν°λ₯Ό λ°μΈλ©νκ³ , λ°μ΄ν°μ λ³νλ₯Ό κ°μ§νλ©΄ νλ©΄μ μ¦μ λ°μνλ κΈ°λ²μ λ§νλ€.

---

## π Instance

`Vue.js`λ₯Ό μ¬μ©νκΈ° μν΄μλ `Vue` μΈμ€ν΄μ€κ° λ°λμ νμνλ©°, μμ±μλ₯Ό μ¬μ©νλ€.

μ΄ μΈμ€ν΄μ€μλ μ¬λ¬κ°μ§ λ©μλκ° μ μλμ΄ μλ€.

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

## π Component

`μ»΄ν¬λνΈ(Component)`λ λͺ¨λ νλ‘ νΈ νλ μμν¬μ νΈλ λμ΄λ€.

HTMLμ μ»΄ν¬λνΈ λ¨μλ‘ μμ±νμ¬ μ¬μ¬μ©μ±μ ν€μ μ΅λν κ²½μ μ μΌλ‘ νλ©΄μ κ΅¬μ±νλ κ²μ΄ λͺ©μ μ΄λ€.

μ΄λ `μ μ­ μ»΄ν¬λνΈ(Global Component)`μ `μ§μ­ μ»΄ν¬λνΈ(Local Component)`λ‘ λλλ©°

`μ μ­ μ»΄ν¬λνΈ`λ λ§ κ·Έλλ‘ `scope`κ° `global`μΈ μ»΄ν¬λνΈλ₯Ό λ§νλ©°,

`μ§μ­ μ»΄ν¬λνΈ`λ κ° μ»΄ν¬λνΈμ `Vue μΈμ€ν΄μ€`μ `components λΈλ‘`μ μ μλ μ»΄ν¬λνΈλ₯Ό λ§νλ€.

`μ§μ­ μ»΄ν¬λνΈ`λ μ§μ­ μ»΄ν¬λνΈκ° μ μλ μ»΄ν¬λνΈμμλ§ `μλͺμ£ΌκΈ°`λ₯Ό κ°λλ€.

μΌλ°μ μΌλ‘ λλΆλΆμ μ€νμμ€ λΌμ΄λΈλ¬λ¦¬κ° `μ μ­ μ»΄ν¬λνΈ`μ ννλ‘ λμ΄μκ³ ,

μΌλ°μ μΈ κ°λ°μκ°`μ μ­ μ»΄ν¬λνΈ`λ₯Ό μ§μ  μμ±νλ κ²½μ°λ λλ¬Όλ©° `μ§μ­ μ»΄ν¬λνΈ`λ₯Ό μμ£Ό λ§μ΄ μ¬μ©νκ² λλ€.

```javascript
// μ μ­ μ»΄ν¬λνΈ
Vue.component('app-header', {
  template: '<h1>Header Component</h1>'
});

// μ§μ­ μ»΄ν¬λνΈ
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

## π Component Communication

![image](https://user-images.githubusercontent.com/71188307/120896133-2204de00-c65b-11eb-9905-e7e3494d3cb5.png)


`Component Communication`μ λ°μ΄ν°μ νλ¦μ μ‘°κΈμ΄λΌλ λ μ½κ² νμνκΈ° μν κ΅¬μ‘°μ΄λ€.

κΈ°λ³Έμ μΈ κ΅¬μ‘°λ νκΈ°μ κ°λ€

μμ μ»΄ν¬λνΈμμ νμ μ»΄ν¬λνΈλ‘λ `props(data)`κ° λ΄λ €κ°λ©°,

νμ μ»΄ν¬λνΈμμ μμ μ»΄ν¬λνΈλ‘λ `event($emit)`κ° μ¬λΌκ°λ€

--- 

## π Axios - HTTP Library

`Axios`λ `Vue.js`μ κ³΅μμ μΈ HTTP Libraryμ΄λ€.

`promise`κΈ°λ°μΌλ‘ λμνλ©°, `CDN`λ°©μμ μ΄μ©νμ¬ λΌμ΄λΈλ¬λ¦¬λ₯Ό μ¬μ©νκ±°λ `NPM`μΌλ‘ μ§μ  μ€μΉνλ λ°©λ²μΌλ‘ λλλ€.

```javascript
// CDN λ°©μ
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script>
  new Vue({
   el: '#app',
   methods: {
     fetch: function() {
          axios.get('https://jsonplaceholder.typicode.com/users/')
               .then(function(response) {
                 console.log(response); // then: ν΅μ  μ±κ³΅μ μ€ν λ  λΈλ‘
               })
               .catch(function(error) {
                 console.log(error); // catch: ν΅μ  μ€ν¨μ μ€ν λ  λΈλ‘
               });
        }
    }
  })
</script>
```

```javascript
// NPM λ°©μ
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
             console.log(response); // then: ν΅μ  μ±κ³΅μ μ€ν λ  λΈλ‘
           })
           .catch(function(error) {
             console.log(error); // catch: ν΅μ  μ€ν¨μ μ€ν λ  λΈλ‘
           });
    }
  }
})
```

---

## π Template syntax

`data-binding`μ `Vue μΈμ€ν΄μ€`μ λ°μ΄ν°μ `HTML`μ λκΈ°νμν€λ μμμ΄λ€.

μλμ μ½λλ₯Ό λ³΄λ©΄ `Vue μΈμ€ν΄μ€`μ `<div id='app'>` κ° μ°κ²°λΌμκ³ , 

`Vue μΈμ€ν΄μ€`μ `data` - `message`κ° `{{ message }}` λΌλ λ¬Έλ²μΌλ‘ λ°μΈλ©μ΄ λμ΄μλ€.

μ΄ μνμμ `message`μ κ°μ΄ λ³κ²½λλ©΄ `HTML`μ μ€μκ°μΌλ‘ λ³κ²½λ κ°μ΄ νμλκ² λλ€.

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

`vue-directive` `v-`λ‘ μμνλ `Vue.js`μ λ¬Έλ²μ μ΄μΉ­νλ€.

μλ₯Ό λ€μλ©΄ `v-on`, `v-if-else`, `v-bind`,`v-model`,`v-show` λ±μ λ§νλ©°,

μμ `data-binding`κ³Ό κ²°ν©νμ¬ κ°λ ₯ν `Reactivity`λ₯Ό λ³΄μ¬μ€λ€.

--- 

## π Vue-CLI

`CLI`λ `Command-line interface`μ μ½μλ€.

`Vue.js`λ₯Ό `NPM`κ³Ό `Webpack`μ μ¬μ©νμ¬ λͺλ Ήμ€ νλμ€λ§μΌλ‘ μ½κ² μ¬μ©ν  μ μκ² ν΄μ£Όλ κ³ κΈκΈ°μ μ΄λ€.

νλ‘μ νΈλ₯Ό μλμΌλ‘ μμ±ν΄μ£Όμ§λ§, νλ‘μ νΈμ κ΅¬μ‘°κ° μ ννλΌμμΌλ―λ‘ μ΄μ λν νμ΅μ΄ νμνλ€.

νλ‘μ νΈλ₯Ό μμ±νκΈ° μν΄μλ `Node.js`μ `NPM`μ΄ μ€μΉλΌμμ΄μΌ νλ©°

μμ±μλ μλμ κ°μ λ²μ μ μ¬μ©νλ€.

```text
npm -v
6.14.13

node -v
v14.17.0

vue --version
@vue/cli 4.5.13
```
 
`Node.js`μ `NPM`μ΄ μ€μΉλΌμλ€λ©΄ `Vue-CLI`λ₯Ό μ€μΉνκΈ° μν΄ μλμ λͺλ Ήμ΄λ₯Ό μλ ₯νλ€.

`-g`λ `OS`μ `Vue-CLI`λ₯Ό μ μ­μΌλ‘ μ€μΉνκ² λ€λ μλ―Έμ΄λ€.

```text
npm install -g @vue/cli
```

μ΄ν `Vue.js` νλ‘μ νΈλ₯Ό μμ±νκΈ° μν λͺλ Ήμ΄λ νκΈ°μ κ°λ€.

```text
cd {projectλ₯Ό μμ±ν  μμΉ}

vue create {project-name}
```

νλ‘μ νΈκ° μμ±λλ©΄ ν°λ―Έλμ μ νμλ λλ‘ 

```text
cd {project-name}

npm run serve
```

λ₯Ό μμ°¨μ μΌλ‘ μλ ₯νλ©΄ `Vue.js` μλ²κ° λ¬λ€.

μμ±λλ νλ‘μ νΈμ κ΅¬μ‘°λ νκΈ°μ κ°λ€.

```text
Project
ββ README.md
ββ .gitignore
ββ babel.config.js
ββ package.json
ββ package-lock.json
ββ public
β  ββ favicon.ico
β  ββ index.html
ββ src
   ββ App.vue
   ββ main.js
   ββ components
   ββ assets
      ββ logo.png
```

--- 

## π Single file component

`Vue-CLI`λ₯Ό μ΄μ©νμ¬ λ§λ  νλ‘μ νΈμλ `.vue`νμ₯μλ₯Ό κ°μ§ νμΌλ€μ΄ μλ€.

μ΄λ₯Ό `μ±κΈνμΌ μ»΄ν¬λνΈ(Single file component)`λΌ λΆλ₯΄λ©°, 

μ΄ `μ±κΈνμΌ μ»΄ν¬λνΈ`λ€μ `Webpack`μ΄ μ μ?μ΄λ΄μ΄ μ¬μ©μλ€μκ² νλ©΄μ λ³΄μ¬μ£Όλ κ²μ΄λ€.

κ³΅λΆλ₯Ό λ ν΄λ΄μΌ κ² μ§λ§ `Webpack`μ `Gradle`κ³Ό λΉμ·ν μ­ν μ νλ€κ³  μκ°λλ©°

`λ°λ²¨(babel)`μ΄λΌκ³  λΆλ₯΄λ κ²μ `javascript`κ° μ€νλλ λ€μν νκ²½μμ

κ° μμ€νλ€μ νΈνμ±μ λ³΄μ₯ν΄μ£ΌκΈ° μν `indirection`μΌλ‘

`Java`μ `JVM`κ³Ό λΉμ·ν μ­ν μ νλ€κ³  μ΄ν΄κ° λλ€.
