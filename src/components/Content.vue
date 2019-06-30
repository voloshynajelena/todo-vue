<template>
  <section class="content">
    <ul>
      <li v-for='(item,index) in todoList' :key="index" v-show='item.visibility'>
        <div>
          <input class="toggle" 
                  type="checkbox" 
                  @change='toggleStatus' 
                  v-model='item.checked'/>
          <label @dblclick="editTodo(index)" v-show="!item.isEdit">{{item.text}}</label>
          <input class="edit" 
                  v-show="item.isEdit" 
                  v-model='item.text' 
                  @keyup.enter="editedTodo(index)"
                  @keyup.esc="editedTodo(index)"/>
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

<style lang="scss" scoped>
ul {
  list-style: none;

  li {
    font-size: 24px;
    border-bottom: 1px solid #ededed;

    &:hover div button {
      display: block;
    }

    div {
      display: flex;
      justify-content: left;
      align-items: center;
      position: relative;
      padding: 10px 0;

      button {
        display: none;
        background-color: transparent;
        border: none;
        font-size: 25px;
        color: tomato;
        font-weight: 100;
        position: absolute;
        right: 0;

        &:hover {
          color: rgb(219, 68, 42)
        }
      }
      input.edit {
          margin-left: 50px;
          height: 30px;
          width: 80%;
          font-size: 20px;
          padding-left: 10px;
      }
      input[type='checkbox'] {
        background: none;
        width: 30px;
        height: 30px;
        opacity: 0;
        position: absolute;
        left: 0;
        z-index: 1;

      }

      label {
        background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' width='40' height='40' viewBox='-10 -18 100 135'%3e%3ccircle cx='50' cy='50' r='50' fill='none' stroke='%23ededed' stroke-width='3'/%3e%3c/svg%3e");
        background-repeat: no-repeat;
        background-position: center left;
        padding-left: 50px;
      }

      input[type='checkbox']:checked + label {
        text-decoration: line-through;
        color: silver;
        background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' width='40' height='40' viewBox='-10 -18 100 135'%3e%3ccircle cx='50' cy='50' r='50' fill='none' stroke='%23bddad5' stroke-width='3'/%3e%3cpath fill='%235dc2af' d='M72 25L42 71 27 56l-4 4 20 20 34-52z'/%3e%3c/svg%3e");
      }
    }
  }
}
</style>
