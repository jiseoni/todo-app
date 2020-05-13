<template>
  <div>
    <!-- <p>{{ msg }}</p>
    <main v-if="show">메인</main> -->
    <todo-header></todo-header>
    <todo-input v-on:addItem="addItem"></todo-input>
    <todo-list :todoItems="todoItems" v-on:removeItem="removeItem"></todo-list>
    <todo-footer v-on:clear="clearItems"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from '@/components/TodoInput.vue'
import TodoList from '@/components/TodoList.vue'
import TodoFooter from '@/components/TodoFooter.vue'
import Vue from 'vue'
export const eventBus = new Vue();


export default {
  components: {
    'todo-header': TodoHeader,
    'todo-input': TodoInput,
    'todo-list': TodoList,
    'todo-footer': TodoFooter
  },
  data() {
    return {
      todoItems: []
    }
  },
  methods: {
    fetchTodoItems: function () {
      for (var i = 0; i < localStorage.length; i++) {
        var value = localStorage.key(i);
        this.todoItems.push(value);
      }
    },
    clearItems: function () {
      localStorage.clear();
      this.todoItems = [];
    },
    removeItem: function (todoItem, index) {
      console.log('clicked', todoItem, index);
      this.todoItems.splice(index, 1);
      localStorage.removeItem(todoItem);
    },
    addItem: function (inputText) {
      localStorage.setItem(inputText, inputText);
      this.todoItems.push(inputText);
    }
  },
  created: function () {
    this.fetchTodoItems();
  }
}
</script>

<style>

</style>