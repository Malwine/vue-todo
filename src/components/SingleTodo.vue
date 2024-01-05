<template>
  <li class="d-flex align-items-center list-group-item">
    <button 
      v-if="!isEditing"
      :class="{completed}"
      @click="$emit('on-toggle')"
      class="btn border-0 text-left flex-grow-1">{{ text }}</button>
    <form v-else @submit.prevent="endEditing()" class="flex-grow-1">
      <input @blur="startEditing()" v-model="newTodoText" type="text" class="form-control">
    </form>
    <i @click="startEditing()" class="fas fa-edit edit-icon-fix"></i>
    <i @click="$emit('on-delete')" class="fas fa-trash-alt delete-icon-fix"></i>
  </li>
</template>

<script>
export default {
  //accept props
  props: {
    text: String,
    completed: Boolean,
  },
  data() {
    return {
      isEditing: false,
      newTodoText: ""
    }
  },
  methods: {
    startEditing(){
      if(!this.isEditing) {
        this.newTodoText = this.text;
        this.isEditing = true;
      } else {
        this.endEditing();
      }
    },
    endEditing(){
      this.isEditing = false;
      this.$emit('on-edit', this.newTodoText);
    }
  }
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
.edit-icon-fix {
  color: #497fba;
  margin-left: 20px;
}
.delete-icon-fix {
  color: #aa414c;
  margin-left: 10px;
}
</style>