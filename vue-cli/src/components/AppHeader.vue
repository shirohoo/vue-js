<template>
  <header>
    <h1>{{ title }}</h1> <!-- 상위 컴포넌트에서 내려온 데이터를 바인딩  -->
    <button v-on:click="sendEvent">send</button> <!-- 버튼 클릭 시 상위 컴포넌트로 이벤트를 전송하는 메서드 실행  -->
  </header>
</template>

<script>
export default {
  props  : ['title'], // 상위 컴포넌트에서 title이라는 이름으로 내려온 데이터
  methods: {
    sendEvent: function(){
      this.$emit('renew') // 상위 컴포넌트로 이벤트 전달 (이벤트 이름=renew)
    }
  }
}
</script>

<!-- scoped는 해당 컴포넌트에서만 css가 적용됨을 의미함  -->
<style scoped>

</style>
