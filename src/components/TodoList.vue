<template>
  <div>
    <ul>
      <TodoItem
        v-for="(todo, index) in todos" :key="index"
        v-bind:todo="todo"
        v-bind:index="index"
        v-on:remove-todo="onRemoveTodo"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'
export default{
  props:['todos'],
  components: {
    TodoItem
  },
  methods: {
    onRemoveTodo(id) {
      this.$emit('remove-todo', id)      
    }
  }
}
</script>
<style scoped>
  ul{
    list-style: none;
    padding: 0;
    margin: 0;
  }
</style>