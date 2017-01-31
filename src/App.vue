<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-md-8">
        <category></category>
      </div>
      <div class="col-md-4">
        <cart :carts="carts"></cart>
      </div>
    </div>


  </div>
</template>

<script>
// import Hello from './components/Hello'
// import Start from './components/Start'
// import StartSample from './components/StartSample'

import Category from './components/Category'
import Cart from './components/Cart'
import EventHub from './EventHub'

export default {
  name: 'app',
  components: {
    // Hello, Start, StartSample
    Category, Cart
  },

  data () {
    return {
      carts: []
    }
  },

  mounted () {
    EventHub.$on('addCart', this.addToCard)
  },

  methods: {
    addToCard (product) {
      this.carts.push(product)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
