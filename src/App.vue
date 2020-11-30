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
    <ul class="list-todo">
      <li v-for="(todo, index) in todoList.value" :key="`todo_${index}`">
        {{ todo }}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent, onMounted } from 'vue';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

export default defineComponent({
  name: 'Home',
  setup() {
    const todoList = ref<string[]>([]);
    const todoText = ref('');
    const addTodoTask = () => {
      todoList.value.push(todoText.value.toString());
    };
    return {
      todoList,
      todoText,
      addTodoTask
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
.list-todo {
  li {
    margin-top: 10px;
  }
}
</style>
