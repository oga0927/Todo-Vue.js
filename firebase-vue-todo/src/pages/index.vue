<template>
  <div>
    <h1>Todoリスト</h1>
    <todo-form @handleParentAddTodo="handleParentAddTodo"/>
    <todo-list
      :todos="todos"
      @handleParentDeleteTodo="handleParentDeleteTodo"
      @handleParentCompleteTodo="handleParentCompleteTodo"/>
  </div>
</template>

<script>
import TodoForm from '@/components/TodoForm'
  ;
import TodoList from '@/components/TodoList'
  ;

export default {
  // コンポーネントの読み込みはcomponentsを使う
  name: 'Todo',
  components: {
    TodoForm,
    TodoList,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    handleParentAddTodo(value) {
      if (value) {
        this.todos.unshift({ text: value, complete: false });
      }
    },
    handleParentDeleteTodo(index) {
      // splice()は第一引数でindexの配列位置を指定して、第二引数で渡した数字の分だけ要素を削除する
      this.todos.splice(index, 1);
    },
    handleParentCompleteTodo(index) {
      this.todos[index].complete = !this.todos[index].complete;
    },
  },
};
</script>

<style scoped>

</style>
