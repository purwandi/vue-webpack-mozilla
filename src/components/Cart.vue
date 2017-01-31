<template>
<table class="table table-bordered">
  <tbody>
    <tr v-for="cart in carts">
      <td>{{ cart.name }}</td>
      <td>{{ cart.price_format }}</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td>{{ carts.length }} item</td>
      <td>{{ total }}</td>
    </tr>
  </tfoot>

</table>
</template>

<script>
export default {
  name: 'cart',
  props: {
    carts: {
      type: Array
    }
  },
  computed: {
    total () {
      if (this.carts.length > 0) {
        return this.carts.reduce((total, key) => {
          let price = key.price_format.replace('Rp ', '').replace('.', '')
          return total + parseFloat(price)
        }, 0)
      }
      return 0
    }
  }
}
</script>
