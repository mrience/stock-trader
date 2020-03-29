<template>
  <div class="container">
    <div class="row">
      <app-stock v-for="stock in stocks" :stock="stock"></app-stock>
    </div>
  </div>
</template>

<script>
  import Stock from './Stock'

    export default {
      name: "Stocks",
      components: {
          appStock: Stock
      },
      computed: {
          stocks() {
            return this.$store.getters.stocks;
          }
      }
    }
</script>

<style scoped>
  .row{
    margin-top: 5%;
  }
</style>
