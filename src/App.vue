<script>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
//import HelloWorld from './components/HelloWorld.vue'
import PictureBook from './components/PictureBook.vue';

export default {
  components: {
    //HelloWorld
    PictureBook
  }
}

</script>

<template>
  <!--<div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>-->
  <!--<HelloWorld msg="Vite + Vue" />-->
  <picture-book></picture-book>
</template>

<style scoped>

</style>
