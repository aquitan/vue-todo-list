<template>
  <form
      @submit.prevent="addItem"
      class="add-item">
    <div class="item-group">
      <input
          v-model="inputLabel"
          class="form-control" type="text">
      <button class="btn btn-primary">Add Item</button>
    </div>
  </form>
</template>

<script>
  export default {
    data() {
      return {
        inputLabel: '',
        id: 100
      }
    },
    methods: {
      addItem() {
        if (this.inputLabel.trim()) {
          const newItem = {
            text: this.inputLabel,
            id: this.id++,
            done: false,
            important: false
          }
          this.$emit('addItem', newItem);
          this.inputLabel = ''
        }
      }
    }
  }

</script>

<style scoped>
  .add-item {
    margin-top: 20px;
  }

  .btn {
    width: 150px;
  }

  .item-group {
    display: flex;
    justify-content: space-between;
  }
</style>