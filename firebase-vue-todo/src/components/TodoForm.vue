<template>
    <!-- Bootstrapがテンプレートを用意している -->
    <b-container>
      <b-input-group>
        <b-form-input type="text" v-model="value"/>
        <b-input-group-append>
          <b-button variant="info" @click="handleAddTodo()">送信</b-button>
        </b-input-group-append>
      </b-input-group>
    </b-container>
</template>

<script>
export default {
  name: 'TodoForm',
  // 入力した値をdataオプションに保存
  data() {
    return {
      value: '',
    };
  },
  methods: {
    handleAddTodo() {
      // $emitで呼び出し後、第一引数に関数名、第二引数に渡したい値
      this.$emit('handleParentAddTodo', this.value);
    },
  },
};
</script>

<style scoped>

</style>
