<template>
  <div class="col-12 col-sm-6 col-md-4 col-lg-4">
    <div class="card">
      <div class="card-header">
        <h4 class="card-title">
          NAME
          <small>(price: PRICE)</small>
        </h4>
      </div>
      <div class="card-body">
        <div class="float-left">
          <input
            type="number"
            class="form-control"
            placeholder="Quantity"
            >
        </div>
        <div class="float-right">
          <button class="btn btn-success">
            Buy
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: "Stock"
    }
</script>

<style scoped>
  .card {
    margin-top: 5%;
  }
</style>
