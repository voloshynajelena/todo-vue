<template>
  <section class="content">
    <ul>
      <li v-for='(item,index) in todoList' :key="index">
        {{item}}
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: 'Content',
  data(){
      return {

      }
    },
    props: {
      todoList: Array
    },
    updated(){
      console.log(this.todoList)
    }
}
</script>

<style scoped>

</style>
