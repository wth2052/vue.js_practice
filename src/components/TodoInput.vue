<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodoList">
    <span class="addContainer" v-on:click="addTodoList">
        <i class="far fa-plus-square addBtn">입력</i>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: ''
    }
  },
  methods: {
    addTodoList: function() {
      console.log(this.newTodoItem);
      //저장
      localStorage.setItem(this.newTodoItem, this.newTodoItem);
      this.clearInput();
    },
      clearInput: function() {
        this.newTodoItem = ""; //다 쓴 후 초기화시켜준다.
    }
  }
}
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #FFC0CB, #FF6781);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>