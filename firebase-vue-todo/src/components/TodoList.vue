<template>
  <b-container>
    <b-row :key="index" v-for="(todo, index) in todos" class="mt-2">
      <b-col cols="8" class="text-left">
        <h5>{{todo.text}}</h5>
      </b-col>
      <b-col cols="4" class="test-right">
        <b-button @click="handleCompleteTodo(index)"></b-button>
        <b-button @click="handleDeleteTodo(index)">削除</b-button>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: 'TodoList',
  props: ['todos'],
  methods: {
    handleDeleteTodo(index) {
      // $emitで呼び出し後、第一引数に関数名、第二引数に渡したい値
      this.$emit('handleParentDeleteTodo', index);
    },
    handleCompleteTodo(index) {
      this.$emit('handleParentCompleteTodo', index);
    },
  },
};
</script>

<style scoped>

</style>
