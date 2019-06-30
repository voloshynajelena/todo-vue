<template>
  <div class="main">
    <h1>{{ msg }}</h1>
    <Header @keyup-enter="addTodo"/>
    <Content :todoList='todoList'/>
    <Footer/>
  </div>
</template>

<script>
import Header from './Header.vue'
import Content from './Content.vue'
import Footer from './Footer.vue'

export default {
  name: 'Main',
  props: {
    msg: String
  },
  data () {
    return {
      todoList: []
    }
  },
  components: {
    Header,
    Content,
    Footer
  },
  methods: {
    addTodo(item){
      this.todoList.push(item)
    }
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
