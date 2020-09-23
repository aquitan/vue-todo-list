<template>
  <li
      :class="{completedTask: item.done, importantTask: item.important}"
      class="list-group-item"
      :item="item">
    <span
        class="task-text"
        :class="{done: item.done, important: item.important}"
        @click="doneItem(item)"
    >{{ item.text | uppercase }}</span>
    <div class="btn-group">
      <button
          @click="importantItem(item)"
          class="btn btn-success">
        <i class="fa fa-exclamation" aria-hidden="true"></i>
      </button>
      <button
          @click="removeItem(item)"
          class="btn btn-danger">
        <i class="fa fa-trash" aria-hidden="true"></i>
      </button>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  methods: {
    doneItem(item) {
      item.done = !item.done
    },
    importantItem(item) {
      item.important = !item.important
    },
    removeItem(item) {
      this.$emit('removeItem', item.id)
    }
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase();
    }
  }
}
</script>

<style scoped>
  .list-group-item {
    display: flex;
    justify-content: space-between;
  }

  .btn {
    width: 50px;
  }
  
  .done {
    text-decoration: line-through;
  }

  .important {
    color: cornflowerblue;
    font-weight: bold;
  }

  .importantTask {
    color: goldenrod;
  }

  .completedTask {
    background-color: rgba(172, 255, 156, 0.5);
  }

  .task-text {
    display: flex;
    align-items: center;
  }
  
  span {
    cursor: pointer;
  }
</style>