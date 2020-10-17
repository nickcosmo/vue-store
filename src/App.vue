<template>
  <app-header></app-header>
  <router-view></router-view>
</template>

<script>
import AppHeader from './components/AppHeader.vue';

export default {
  components: {
    AppHeader,
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  background-color: #EDF5E1;
  font-family: Arial, Helvetica, sans-serif;
}
</style>
