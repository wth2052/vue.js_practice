<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodoList">
    <!-- <button v-on:click="addTodo">add</button> -->
    <span class="addContainer" v-on:click="addTodoList">
        <i class="fas fa-plus addBtn" aria-hidden="true"></i>
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
      if (this.newTodoItem !== '') {
        let obj = {completed: false, item: this.newTodoItem};
        // text/text가 아닌 text/boolean 값을 저장, 텍스트/완료여부
        localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
        this.clearInput();
      }
    },
      clearInput: function() {
        this.newTodoItem = ''; //다 쓴 후 초기화시켜준다.
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