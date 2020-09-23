<template>
  <div>
    <h2>Todo List</h2>
    <span>Items to do: {{todosLeft}}</span>
  </div>
</template>

<script>
  export default {
    props: ['todosLeft']
  }
</script>