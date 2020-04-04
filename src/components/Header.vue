<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <router-link to="/" class="navbar-brand">Stock Trader</router-link>

    <div class="collapse navbar-collapse">
      <ul class="nav navbar-nav mr-auto">
        <router-link class="nav-item" to="/portfolio" active-class="active" tag="li"><a class="nav-link">Portfolio</a></router-link>
        <router-link class="nav-item" to="/Stocks" active-class="active" tag="li"><a class="nav-link">Stocks</a></router-link>
      </ul>
      <strong class="navbar-text navbar-right">Funds: {{funds}}</strong>
      <ul class="nav navbar-nav navbar-right">
        <li><a href="#" class="nav-link">End Day</a></li>
        <li class="dropdown">
          <a
            href="#"
            class="dropdown-toggle nav-link"
            data-toggle="dropdown"
            role="button"
            aria-haspopup="true"
            aria-expanded="false">Save & Load <span class="caret"></span>
          </a>
          <ul class="dropdown-menu">
            <li><a href="#">Save Data</a></li>
            <li><a href="#">Load Data</a></li>
          </ul>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
    export default {
      name: "Header",
      computed: {
        funds() {
          return this.$store.getters.funds
        }
      }
    }
</script>

<style scoped>

</style>
