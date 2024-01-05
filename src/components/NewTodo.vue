<template>
  <form @submit.prevent="addTodo()" class="col-12 col-lg-6 form-fix">
    <input v-model="newTodo" placeholder="Enter todo" type="text" class="form-control">
  </form>

</template>

<script>
export default {
  data() {
    return {
      newTodo: ""
    }
  },
  methods: {
    addTodo() {
      if(this.newTodo.length>1){
        this.$emit("on-addtodo", this.newTodo)
      }
      this.newTodo = ""
    }
  }
}
</script>

<style scope>
.form-fix {
  padding-left: 0px;
  margin-bottom: 20px;
}
</style>