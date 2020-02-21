<template>
  <div id="app">
    <gallery></gallery>
  </div>
</template>

<script>
import gallery from './components/mini-gallery.vue'
export default {
  components:{
    gallery
  },
}
</script>

<style lang="scss">
#app {
  padding: 2rem;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  margin: auto 0;
 
}
body{
   background-color: #f2f2f2;
}

</style>
