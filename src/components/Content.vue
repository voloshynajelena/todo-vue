<template>
  <section class="content">
    <ul>
      <li v-for='(item,index) in todoList' :key="index">
        <div>
          <input class="toggle" 
                  type="checkbox" 
                  @change='toggleStatus' 
                  v-model='item.checked'/>
          <label @dblclick="editTodo(index)" v-show="!item.isEdit">{{item.text}}</label>
          <input v-show="item.isEdit" v-model='item.text' @keyup.enter="editedTodo(index)"/>
          <button @click='removeItem(index)'>&times;</button>
        </div>
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
    methods: {
      removeItem(elem){
        this.$emit('remove-item',elem)
      },
      toggleStatus(index){
        this.$emit('toggle-status',index)
      },
      editTodo(index){
        this.$emit('edit-item',index)
      },
      editedTodo(index){
        this.$emit('edited-item',index)
      }
    }
}
</script>

<style scoped>

</style>
