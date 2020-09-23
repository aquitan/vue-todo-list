<template>
  <ul class="list-group">
    <TodoListItem
        @removeItem="removeItem"
        v-for="item in todos"
        :item="item"
        :key="item.id"
    />
  </ul>
</template>
<script>
import TodoListItem from "@/components/TodoListItem";
export default {
  props: ['todos'],
  components: {
    TodoListItem
  },
  methods: {
    removeItem(id) {
      this.$emit('removeItem', id)
    }
  }
}
</script>