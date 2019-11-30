<template>
  <li>
    <span :class="{ done: todo.completed}">
      <input type="checkbox" v-on:change="todo.completed = !todo.completed"> 
      <strong>{{ index + 1 }}</strong>
      {{ todo.title | uppercase }}
    </span>
    <button
      class="remove"
      v-on:click="$emit('remove-todo', todo.id)">&times;</button>
    
  </li>
</template>
<script>
export default{
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase()
    }
  }
}
</script>
<style scoped>
li{
  border: 1px solid #ccc;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.5rem 1rem;
  margin-bottom: 1rem;
  border-spacing: 5px;
}
input{
  margin-right:1rem ;
}
.remove{
  background-color: red;
  color: #fff;
  border-radius: 50%;
  font-weight: 700;
  font-size: 2rem;
  line-height: 1.95rem;
  width: 2rem;
  height: 2rem;
  border: 1px solid #fff;
  transition: all 0.3s;
  cursor: pointer;
}
.remove:hover{
  color: red;
  background-color: #fff;
  border-color: red;
}
.done{
  text-decoration: line-through;
}
</style>