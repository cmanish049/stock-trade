<template>
  <div>
  <h1>Home Component</h1>
  <p>My funds: {{ funds | currency }}</p>
  </div>
</template>

<script>
export default {
  computed: {
    funds() {
      return this.$store.getters.funds;
    }
  },
}
</script>

<style>

</style>