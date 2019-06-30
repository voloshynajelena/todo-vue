<template>
  <header>
    <input  class="new-todo" autofocus autocomplete="off" placeholder="New todo" v-model='newTodo' @keyup.enter="sendEvent"/>
  </header>
</template>

<script>
/* eslint-disable */
export default {
  name: 'Header',
  data(){
      return {
          newTodo: ''
      }
  },
  methods: {
      sendEvent(){
        this.$emit('keyup-enter',this.newTodo)
      }
  }
}
</script>

<style lang="scss" scoped>
  header {
    padding-left: 40px;
    
    input {
      width: 90%;
      height: 40px;
      padding-left: 20px;
      font-size: 20px;
    }
  }
</style>
