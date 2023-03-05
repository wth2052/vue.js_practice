<template>
  <div>
    <ul>
      <li v-for="(todoItem, index) in propsdata" class="shadow" v-bind:key="todoItem.item">
        <span class="checkBtn" v-on:click="checkTodoList(todoItem)">
          <i class="fas fa-check"></i>
        {{ todoItem }}
        <span class="removeBtn" v-on:click="removeTodoList(todoItem, index)">
          <i class="fas fa-trash-alt"></i>
        </span>
      </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      todoItems: []
    }
  },
  props: ['propsdata'],
methods: {
    removeTodoList: function(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1); //특정 index에서 하나를 지운다.
    },
  checkTodoList: function (todoItem) {
    todoItem.completed = !todoItem.completed;
    localStorage.removeItem(todoItem.item);
    localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
  }
  },
created: function() {
  if (localStorage.length > 0) {
    for (let i = 0; i < localStorage.length; i++) {
      //찍먹이 첨이라 저 loglevel:webpack-dev-server가 뭔지 모르겠다. 찾아보니 로컬에서 개발 서버를 실행하기 위해 사용하는 도구란다
      if (localStorage.key(i) !== 'loglevel:webpack-dev-server') {
        this.todoItems.push(localStorage.key(i));
      }
    }
  }
}
}
</script>


<style scoped>
ul {
  list-style-type: none;
  padding-left: 0;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}

</style>
