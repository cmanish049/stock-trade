<template>
  <div class="container">
    <app-header></app-header>
    <router-view />
  </div>
</template>
<script>
import Header from './components/Header'
export default {
  components: {
    appHeader: Header
  },
  mounted() {
    this.$store.dispatch('initStocks');
  }
}
</script>
<style>
</style>
