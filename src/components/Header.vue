<template>
  <div>
    <router-link class="view-link" to="/">Back to Home Page</router-link>
    <h2>Todo List</h2>
    <span>Items to do: {{todosLeft}}</span>
  </div>
</template>

<script>
  export default {
    props: ['todosLeft']
  }
</script>
