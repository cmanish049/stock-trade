<template>
  <div class="row">
    <app-stock v-for="stock in stocks" :key="stock.id"></app-stock>
  </div>

</template>

<script>
import Stock from "./Stock";
export default {
  components: {
    appStock: Stock,
  },
  data() {
    return {
      stocks: [
        {id: 1, name:'MeroBhakaari', price: 110},
        {id: 2, name:'Spinel Tech', price: 100},
        {id: 3, name:'Isop Nepal', price: 120},
        {id: 4, name:'Neptrox', price: 150},
      ]
    };
  },
}
</script>

<style>

</style>