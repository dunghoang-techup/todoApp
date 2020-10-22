<template>
  <form class="col-12" @submit.prevent="addTodo($event)">
    <input
        v-model="newTodo"
        type="text"
        class="form-control"
        placeholder="input your mission"
    >
    <button class="btn btn-primary" type="submit" >+</button>
  </form>

</template>

<script>
export default {
  name: "createTodo",
  data() {
    return {
      newTodo: ""
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.length > 0) {
        this.$emit("on-new-todo", this.newTodo);
      }
      this.newTodo = "";
    }
  }
}
</script>

<style lang="scss" scoped>
  form {
    display: flex;
    justify-content: center;
    input {
      height: 35px;
    }
    button {
      margin-left: 5px
    }
  }
</style>