<template>
  <div>
    <ul>
      <li v-for="(todoItem, index) in propsdata" class="shadow" v-bind:key="todoItem.item">
      <span class="checkBtn" v-on:click="toggleComplete(todoItem, index)">
        <i class="fas fa-check"></i>
        {{ todoItem.item }}
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

  props: ['propsdata'],
  methods: {
    removeTodoList: function(todoItem, index) {
      this.$emit('removeItem', todoItem, index);
    },
    toggleComplete: function(todoItem) {
      todoItem.completed = !todoItem.completed;

      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
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
