<template>
  <div class="col-12 col-sm-6 col-md-4 col-lg-4">
    <div class="card">
      <div class="card-header">
        <h4 class="card-title">
          {{stock.name}}
          <small>(price: {{stock.price}})</small>
        </h4>
      </div>
      <div class="card-body">
        <div class="float-left">
          <input
            type="number"
            class="form-control"
            placeholder="Quantity"
            v-model="quantity"
            :class="{danger: insufficientFunds}"
            >
        </div>
        <div class="float-right">
          <button
            class="btn btn-success"
            @click="buyStock"
            :disabled="insufficientFunds || isDisabled"
            >
            {{insufficientFunds ? 'Insufficient Funds': 'Buy'}}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
      name: "Stock",
      props: ['stock'],
      data() {
        return {
          quantity: 0
        }
      },
      computed: {
          funds() {
            return this.$store.getters.funds
          },
          isDisabled: function() {
            return this.quantity <= 0 || !Number.isInteger(+this.quantity)
          },
          insufficientFunds() {
            return this.quantity * this.stock.price > this.funds;
          }
      },
      methods: {
        buyStock(){
            const order = {
              stockId: this.stock.id,
              stockPrice: this.stock.price,
              quantity: this.quantity
            };
            console.log(order);
            this.$store.dispatch('buyStock', order)
            this.quantity = 0;
        }
      }
    }
</script>

<style scoped>
  .card {
    margin-top: 5%;
  }
</style>
