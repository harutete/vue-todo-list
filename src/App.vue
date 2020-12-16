<template>
  <div class="wrapper">
    <h1>Todo List</h1>
    <div class="content-todo-input-wrap">
      <div class="content-todo-input-item">
        <input type="text" v-model="todoText" class="input-add-todo" />
      </div>
      <div class="content-todo-input-item">
        <button type="button" @click="addTodoTask()" class="button-add-todo">
          Add Todo
        </button>
      </div>
    </div>
    <ul class="list-todo" v-if="todoList.length">
      <li
        v-for="(todo, index) in todoList"
        :ref="todoList"
        :key="`todo_${index}`"
      >
        <p>{{ todo }}</p>
        <button
          type="button"
          @click="removeTodoTask(index)"
          class="button-remove-todo"
        >
          Remove
        </button>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { ref, onBeforeUpdate, onUpdated, defineComponent } from 'vue';
import HelloWorld from '@/components/HelloWorld.vue';

export default defineComponent({
  name: 'TodoApp',
  setup() {
    const todoList = ref<string[]>([]);
    const todoText = ref('');
    const addTodoTask = () => {
      todoList.value.push(todoText.value.toString());
      todoText.value = '';
    };
    const removeTodoTask = (index: number) => {
      todoList.value.splice(index, 1);
    };
    return {
      todoList,
      todoText,
      addTodoTask,
      removeTodoTask
    };
  }
});
</script>

<style lang="scss">
body {
  background: #f7f3dc;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #724c25;
}
.content-todo-input-wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: -10px;
  .content-todo-input-item {
    margin-right: 10px;
  }
}
.input-add-todo {
  display: inline-block;
  border: 1px solid #724c25;
  border-radius: 4px;
  padding: 10px 15px;
}
.button-add-todo {
  cursor: pointer;
  display: inline-block;
  background: #f0c060;
  border: none;
  border-radius: 4px;
  color: #ffffff;
  padding: 10px 15px;
}
.button-remove-todo {
  cursor: pointer;
  background: #cccccc;
  border: none;
  border-radius: 4px;
  color: #ffffff;
  font-size: 12px;
  padding: 5px 10px;
}
.list-todo {
  list-style: none;
  li {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 10px;
    margin-right: -10px;
    & * {
      margin-right: 10px;
    }
  }
}
</style>
