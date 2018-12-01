<template>
  <div id="app">
    <router-view/>
    <DropDownMenu></DropDownMenu>
  </div>
</template>

<script>
  /* eslint-disable no-trailing-spaces */

  import DropDownMenu from '@/components/DropDownMenu.vue';

  export default {
    name: 'App',
    components: {
      DropDownMenu
    }
  }
</script>

<style>
  #app {
    font-family:  Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  body {
    margin: 0px;
    height: 300px
  }
</style>
