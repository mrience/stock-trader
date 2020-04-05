<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <router-link to="/" class="navbar-brand">Stock Trader</router-link>

    <div class="collapse navbar-collapse">
      <ul class="nav navbar-nav mr-auto">
        <router-link class="nav-item" to="/portfolio" active-class="active" tag="li"><a class="nav-link">Portfolio</a></router-link>
        <router-link class="nav-item" to="/Stocks" active-class="active" tag="li"><a class="nav-link">Stocks</a></router-link>
      </ul>
      <strong class="navbar-text navbar-right">Funds: {{funds | currency}}</strong>
      <ul class="nav navbar-nav navbar-right">
        <li><a href="#" class="nav-link" @click="endDay">End Day</a></li>
        <li
          class="dropdown"
          :class="{open: isDropdownOpen}"
          @click="openDropdown"
        >
          <a
            href="#"
            class="dropdown-toggle nav-link"
            data-toggle="dropdown"
            role="button"
            aria-haspopup="true"
            aria-expanded="false">Save & Load <span class="caret"></span>
          </a>
          <ul class="dropdown-menu">
            <li><a class="dropdown-item" href="#">Save Data</a></li>
            <li><a class="dropdown-item" href="#">Load Data</a></li>
          </ul>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
  import {mapActions} from 'vuex'

    export default {
    data() {
      return {
        isDropdownOpen: false
      }
    },
      name: "Header",
      computed: {
        funds() {
          return this.$store.getters.funds
        }
      },
      methods: {
        ...mapActions([
          'randomizeStocks'
        ]),
        endDay() {
          this.randomizeStocks();
        },
        openDropdown() {
          return !this.isDropdownOpen;
        }
      }
    }
</script>

<style scoped>

</style>
