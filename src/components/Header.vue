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

<style scoped>

</style>
