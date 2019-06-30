<template>
  <div class="main">
    <h1>{{ msg }}</h1>
    <Header @keyup-enter="addTodo" />
    <Content
      @remove-item="removeTodo"
      @toggle-status="updateStatus"
      @edit-item="editTodo"
      @edited-item="editTodo"
      :todoList="todoList"
    />
    <Footer 
      @change-filter="updateFilter" 
      @delete-completed="deleteCompleted" 
      :todoListLength="activeItemsLength" />
  </div>
</template>

<script>
/* eslint-disable */
import Header from "./Header.vue"
import Content from "./Content.vue"
import Footer from "./Footer.vue"

export default {
  name: "Main",
  props: {
    msg: String
  },
  data() {
    return {
      todoList: []
    };
  },
  components: {
    Header,
    Content,
    Footer
  },
  computed: {
    activeItemsLength(){
      return this.todoList.filter(item=>!item.checked).length
    }
  },
  methods: {
    addTodo(text) {
      let item = { checked: false, text, isEdit: false, visibility: true };
      this.todoList.push(item);
    },
    removeTodo(index) {
      this.todoList.splice(index, 1);
    },
    updateStatus() {
    },
    editTodo(index) {
      this.todoList[index].isEdit = !this.todoList[index].isEdit
    },
    updateFilter(filterName) {
      switch (filterName) {
        case "All":
          this.todoList.map(item=>{
            item.visibility = true
          })
          break
        case "To do":
          this.todoList.map(item=>{
            item.visibility = !item.checked
          })
          break
        case "Done":
          this.todoList.map(item=>{
            item.visibility = item.checked
          })
          break
      }
    },
    deleteCompleted(){
      this.todoList = this.todoList.filter((item,index)=>
        !item.checked
      )
    }
  }
};
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
