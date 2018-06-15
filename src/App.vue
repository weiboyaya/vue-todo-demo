<template>
  <div id="app">
    <Head></Head>
    <Todo></Todo>  
    <Footer></Footer>
  </div>
</template>

<script>
import Head from './components/Head.vue'
import Footer from './components/Footer.vue'
import Todo from './components/todo/Todo.vue'

export default {
  components:{
    Head,
    Footer,
    Todo
  }
}
</script>

<style>
#app{
  position:fixed;
  box-shadow: 0 0 0 50vmax rgba(0, 0, 0, 0.8);
  height: 100%;
  width: 100%;
  overflow: scroll;
}
</style>
