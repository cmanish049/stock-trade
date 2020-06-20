<template>
  <div class="col-sm-6 col-md-4 mt-2 mb-2">
    <div class="card border-success">
    <div class="card-header">
      {{ stock.name }}
      <small>({{ stock.price }})</small>
    </div>
    <div class="card-body  text-success">
      <div class="float-left">
        <input 
          type="number"
          class="form-control"
          placeholder="Quantity"
          v-model.number="quantity"
          >
      </div>
      <div class="float-right">
        <button class="btn btn-success" @click="buyStock" :disabled="quantity <= 0 || !Number.isInteger(quantity)">Buy</button>
      </div>
    </div>
</div>
  </div>
</template>

<script>
export default {
  props: ['stock'],
  data() {
    return {
      quantity: 0,
    };
  },
  methods: {
    buyStock() {
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
      }
      console.log(order);
      this.quantity = 0;
    }
  }
}
</script>

<style>

</style>