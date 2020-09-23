<template>
  <div id="app" class="container">
    <Header :todosLeft="todosLeft"/>
    <SortItems
        @allItems="allItems"
        @onImportant="onImportant"
        @onItemDone="onItemDone"
        :todos="todos"
        :filter="filter"
    />
    <TodoList
        v-if="filteredTodos.length"
        @removeItem="removeTodoItem"
        :todos="filteredTodos"
    />
    <p class="add-todos" v-else>Add Some Todos!</p>
    <AddItem
        @addItem="addItem"
        :todos="todos"
    />
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddItem from "@/components/AddItem";
import SortItems from "@/components/SortItems";
import Header from "@/components/Header";

export default {
  data() {
    return {
      todos: [
        {text: 'Rule', id: 1, done: false, important: false}
      ],
      filter: 'all'
    }
  },
  components: {
    AddItem,
    TodoList,
    SortItems,
    Header
  },
  methods: {
    addItem(todoItem) {
      this.todos.push(todoItem);
    },
    removeTodoItem(id) {
      let index = this.todos.findIndex((el) => el.id === id);
      this.todos = [...this.todos.slice(0, index), ...this.todos.slice(index + 1)];
    },
    onItemDone(filterProp) {
      this.filter = filterProp
      console.log('Filter---', this.filter)

    },
    allItems(filterProp) {
      this.filter = filterProp
      console.log('Filter---', this.filter)
    },
    onImportant(filterProp) {
      this.filter = filterProp
      console.log('Filter---', this.filter)
    }
  },
  computed: {
    todosLeft() {
      return this.todos.filter(item => !item.done).length
    },
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos
      } else if (this.filter === 'done') {
        return this.todos.filter(item => item.done);
      } else if (this.filter === 'important') {
        return this.todos.filter(item => item.important);
      }

      return this.todos
    }
  }
}

</script>

<style>
  .add-todos {
    text-align: center;
  }
</style>
