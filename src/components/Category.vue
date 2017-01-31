<template>
  <div class="row">
    <div class="col-md-4" v-for="product in products">
      <img v-bind:src="product.image.m_ecs" class="img-responsive">
      <p>{{ product.name }}</p>
      <p>{{ product.price_format }}</p>
      <button class="btn btn-success" @click="addToCard(product)">Buy</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import EventHub from '../EventHub'
export default {
  name: 'category',
  data () {
    return {
      search: '',
      products: []
    }
  },
  mounted () {
    this.fetch()
  },

  methods: {
    fetch () {
      axios
        .get('https://ta.tokopedia.com/promo/v1.1/display/products?dep_id=1758&src=directory&item=10&user_id=0&device=desktop')
        .then(response => {
          this.products = response.data.data.map(item => {
            return item.product
          })
        })
        .catch(error => {
          console.log(error)
        })
    },
    addToCard (product) {
      EventHub.$emit('addCart', product)
    }
  },

  computed: {
    filtered () {
      if (this.search) {
        return this.products.filter(item => {
          return item.name.includes(this.search)
        })
      }
      return this.products
    }
  }
}
</script>

<style scoped>
  .img-responsive {
    margin-bottom: 20px;
    overflow: hidden;
    height: 200px;
  }
  .col-md-4 {
    height: 420px;
  }
</style>
