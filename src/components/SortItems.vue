<template>
  <div class="btn-group filters">
    <button
        @click="onItemDone"
        class="btn btn-info">Done</button>
    <button
        @click="onImportant"
        class="btn btn-info">Important</button>
    <button
        @click="allItems"
        class="btn btn-info">All</button>
  </div>
</template>

<script>
  export default {
    props: {
      todos: {
        type: Array,
        required: true
      }
    },
    methods: {
      onItemDone() {
        this.$emit('onItemDone', 'done')
      },
      allItems() {
        this.$emit('allItems', 'all')
      },
      onImportant() {
        this.$emit('onImportant', 'important')
      }
    }
  }
</script>

<style>
  .filters {
    margin: 20px 0;
  }
</style>