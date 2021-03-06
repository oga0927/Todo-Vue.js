<template>
  <b-container>
    <b-row :key="index" v-for="(todo, index) in todos" class="mt-2">
      <!-- 動的なクラスを追加する場合、オブジェクトにクラスを含み真偽値によって制御することができる -->
      <b-col cols="8" :class="[{line: todo.complete}, 'text-left']">
        <h5>{{todo.text}}</h5>
      </b-col>
      <b-col cols="4" class="test-right">
        <!-- ステータスによって完了、未完了とテキスト変更 -->
        <b-button
          @click="handleCompleteTodo(index)"
          :variant="todo.complete ? '' : 'success'">
          {{todo.complete ? '完了' : '未完了'}}
        </b-button>
        <b-button @click="handleDeleteTodo(index)" variant="danger">削除</b-button>
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
/* 現在のコンポーネントの要素のみに反映させる */
  .line {
    text-decoration: line-through;
  }
</style>
