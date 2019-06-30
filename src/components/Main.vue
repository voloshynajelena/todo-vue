<template>
  <div class="main">
    <h1>{{ msg }}</h1>
    <Header title="This is Header"/>
    <Content title="This is Content"/>
    <Footer title="This is Footer"/>
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
  components: {
    Header,
    Content,
    Footer
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
