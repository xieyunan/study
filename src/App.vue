<template>
  <div id="app">
    <Header></Header>
    <ToDo></ToDo>
    <Footer></Footer>
    <router-view/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import ToDo from './components/todo.vue'
export default {
  name: 'App',
  data(){
    return{

    }
  },
  components:{
    Header,
    Footer,
    ToDo
  }
}
</script>

<style scoped>

</style>
