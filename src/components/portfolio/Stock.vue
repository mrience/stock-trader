<template>
  <div class="col-12 col-sm-6 col-md-4 col-lg-4">
    <div class="card">
      <div class="card-header">
        <h4 class="card-title">
          {{stock.name}}
          <small>(price: {{stock.price}}) | Quantity: {{stock.quantity}}</small>
        </h4>
      </div>
      <div class="card-body">
        <div class="float-left">
          <input
            type="number"
            class="form-control"
            placeholder="Quantity"
            v-model="quantity"
          >
        </div>
        <div class="float-right">
          <button
            class="btn btn-success"
            @click="sellStock"
            :disabled="insufficientQuantity || isDisabled"
          >
            {{insufficientQuantity ? 'Not enough Stocks': 'Sell'}}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import {mapActions} from 'vuex'

  export default {
    name: "Stock",
    props: ['stock'],
    data() {
      return {
        quantity: 0
      }
    },
    computed: {
      isDisabled: function() {
        return this.quantity <= 0 || !Number.isInteger(+this.quantity)
      },
      insufficientQuantity() {
        return this.quantity > this.stock.quantity;
      }
    },
    methods: {
      ...mapActions({
        placeSellOrder: 'sellStock'
      }),
      sellStock() {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: this.quantity
        };
        this.placeSellOrder(order);
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
