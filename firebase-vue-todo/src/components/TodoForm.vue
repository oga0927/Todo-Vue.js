<template>
  <div>
    <b-containaer>
      <b-input-group>
        <b-form-input type="text" v-model="value" />
        <b-input-group-append>
          <b-button variant="info" @click="handleAddTodo()">追加</b-button>
        </b-input-group-append>
      </b-input-group>
    </b-containaer>
  </div>
</template>

<script>
export default {
  name: 'TodoFrom',
  data() {
    return {
      value: '',
    };
  },
  methods: {
    handleAddTodo() {
      this.$emit('handleParentAddTodo', this.value);
    },
  },
};
</script>

<style scoped>

</style>
