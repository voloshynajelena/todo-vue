<template>
  <footer>
    <span>{{todoListLength}} {{plural(todoListLength)}} to do</span>
    <ul class="filters">
      <li
        v-bind:class="{active: item.isActive }"
        v-for="(item, index) in filters"
        :key="index"
        @click="filterList(index)"
      >{{item.name}}</li>
    </ul>
    <button @click='deleteCompleted'>
      Delete complited
    </button>
  </footer>
</template>

<script>
/* eslint-disable */
export default {
  name: "Footer",
  data() {
    return {
      text: "item",
      filters: [
        {
          name: "All",
          isActive: true
        },
        {
          name: "To do",
          isActive: false
        },
        {
          name: "Done",
          isActive: false
        }
      ]
    };
  },
  props: {
    todoListLength: Number
  },
  methods: {
    plural: function(count) {
      return this.text + (count === 1 ? "" : "s");
    },
    deleteCompleted(){
      this.$emit('delete-completed')
    },
    filterList(index) {
      this.filters.map((item, number) => {
        if (number == index) {
          item.isActive = true;
          this.$emit("change-filter", item.name)
        } else {
          item.isActive = false;
        }
      });
    }
  }
};
</script>

<style lang="scss" scoped>

$font-stack:    Helvetica, sans-serif;
$primary-color: #333;
$primary-back-color: rgb(255, 255, 255);

@mixin transition($property) {
  -webkit-transition: $property;
  -ms-transition: $property;
  transition: $property;
}

footer {
  display: flex;
  justify-content: space-around;
  align-items: center;
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
    display: flex;
    justify-content: center;
  }

  li {  
    display: flex;
    padding: 6px 12px;
    margin: 20px;
    text-decoration: none;
    cursor: pointer;
    border: 1px solid rgb(228, 228, 228);
    @include transition(all 0.3s); 

      &:hover:not(.active) {
        border: 1px solid rgb(204, 184, 184);
      }
  }

  .active { 
    border: 1px solid rosybrown;
    }

  button {
    background-color: transparent;
    border: none;
    cursor: pointer;

    &:hover {
      text-decoration: underline
    }
  }
}
</style>
