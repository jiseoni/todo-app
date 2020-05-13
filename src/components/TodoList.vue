<template>
  <div>
    {{ todoItems }}
    <ul>
      <li v-for="(todoItem, index) in todoItems" v-bind:key="index">
        {{ todoItem }}
        <button v-on:click="removeItem(todoItem, index)">remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['todoItems'],
  methods: {
    removeItem: function (todoItem, index) {
      this.$emit('removeItem', todoItem, index);
      // console.log('clicked', todoItem, index);
      // this.todoItems.splice(index, 1);
      // localStorage.removeItem(todoItem);
    }
  }
}
</script>

<style>

</style>