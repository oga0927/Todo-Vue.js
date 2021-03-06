<template>
  <div>
    <h1>Todoリスト</h1>
    <todo-form @handleParentAddTodo="handleParentAddTodo"/>
    <todo-list :todos="todos" />
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
        this.todos.unshift({ text: value });
      }
    },
    handleParentDeleteTodo(index) {
      // splice()は第一引数でindexの配列位置を指定して、第二引数で渡した数字の分だけ要素を削除する
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style scoped>

</style>
