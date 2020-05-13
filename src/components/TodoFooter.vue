<template>
  <button @click="$emit('clear')">전체 삭제</button>
</template>

<script>
export default {
    methods: {
        // removeAllItems: function () {
        //     this.$emit('clear');
        // }
    }
}
</script>

<style>

</style>