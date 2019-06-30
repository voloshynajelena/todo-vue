<template>
  <div class="main">
    <h1>{{ msg }}</h1>
    <Header @keyup-enter='addTodo'/>
    <Content @remove-item='removeTodo' 
              @toggle-status='updateStatus'
              @edit-item='editTodo'
              @edited-item='editTodo'
            :todoList='todoList'/>
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
    addTodo(text){
      let item = {checked: false, text, isEdit: false}
      this.todoList.push(item)
    },
    removeTodo(index){
      this.todoList.splice(index,1)
    },
    updateStatus(){
      console.log('updateStatus() todoList----->',this.todoList)
    },
    editTodo(index){
      this.todoList[index].isEdit = !this.todoList[index].isEdit
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
