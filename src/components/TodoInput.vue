<template>
  <div>
      <input type="text" v-model="inputText" v-on:keyup.enter="addItem">
      <button v-on:click="addItem">add</button>
  </div>

</template>

<script>
export default {
    data() {
        return {
            inputText: ''
        }
    },
    methods: {
        addItem: function () {
            // localStorage.setItem(this.inputText, this.inputText)
            this.$emit('addItem', this.inputText);
            this.inputText = '';
        }
    }
}
</script>

<style>

</style>