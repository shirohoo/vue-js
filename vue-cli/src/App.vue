<template>
  <!-- 하위 컴포넌트에서 renew라는 이름으로 올라오는 이벤트를 캐치하면 renewStr이라는 메서드가 동작함 -->
  <!-- 자신의 데이터 title을 하위 컴포넌트에 title이라는 이름으로 내려 줌 -->
  <!-- 하위 컴포넌트는 props 블럭에 title이라는 이름으로 선언하여 이 데이터를 바인딩 할 수 있다 -->
  <AppHeader
      v-on:renew="renewStr"
      v-bind:title="title" />
</template>

<script>
import AppHeader from "./components/AppHeader";

export default {
  data      : function(){
    return {
      title: 'Hello Vue.js !'
    }
  },
  components: {
    AppHeader,
  },
  methods   : {
    renewStr: function(){
      this.title += 'r';
    }
  }
}
</script>

<style>
</style>
