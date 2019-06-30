<template>
  <footer>
    <span>{{todoListLength}} {{plural(todoListLength)}}</span>
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

<style scoped>
</style>
