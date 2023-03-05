<template>
<div class="clearAllContainer">
  <span class="clearAllBtn" v-on:click="clearTodoList">전부 삭제
  </span>
</div>
</template>


<script>
export default {
  methods: {
    clearTodoList: function() {
      this.$emit('clearAll');
    }
  }
}
</script>
<style scoped>
.clearAllContainer {
  width: 8.5rem;
  height: 50px;
  line-height: 50px;
  background-color: white;
  border-radius: 5px;
  margin: 0 auto;
}
.clearAllBtn {
  color: #FF6781;
  display: block;
}
</style>