<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <router-link to="/" class="navbar-brand">Stock Trader</router-link>
    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <router-link to="portfolio" class="nav-item" activeClass="active" tag="li">
          <a class="nav-link" href="#">
            Portfolio
            <span class="sr-only">(current)</span>
          </a>
        </router-link>
        <router-link to="stocks" class="nav-item" activeClass="active" tag="li">
          <a class="nav-link" href="#">Stocks</a>
        </router-link>
      </ul>
      <ul class="navbar-nav navbar-right">
        <li class="nav-item">
          <a class="nav-link" href="#" @click.prevent="endDay">End Day</a>
        </li>
        
        
        <li 
          class="nav-item dropdown">
          <a
            class="nav-link dropdown-toggle"
            href="#"
            id="navbarDropdown"
            role="button"
            data-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
          >Save & Load</a>
          <div class="dropdown-menu" aria-labelledby="navbarDropdown">
            <a class="dropdown-item" href="#" @click.prevent="saveData">Save Data</a>
            <a class="dropdown-item" href="#"  @click.prevent="loadData">Load Data</a>
          </div>
        </li>
        <li class="nav-item">
          <strong class="nav-link">Fund: {{ fund | currency }}</strong>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {

  computed: {
    fund() {
      return this.$store.getters.funds;
    }
  },
  methods: {
    endDay() {
      this.$store.dispatch('randomizeStocks')
    },
    saveData() {
      const data = {
        funds: this.$store.getters.funds,
        stockPortfolio: this.$store.getters.stockPortfolio,
        stocks: this.$store.getters.stocks
      };
      this.$http.put('data.json', data);
    },
    loadData() {
      this.$store.dispatch('loadData');
    },
  }
};
</script>

<style>
</style>