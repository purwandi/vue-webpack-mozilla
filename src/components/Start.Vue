<template>
  <div class="hello">
    {{ helo }}
  </div>
</template>

<script>
export default {
  name: 'Start',
  data () {
    return {
      helo: 'Ini merupakan hello'
    }
  }
}
</script>

<style>
  .hello {
    color: red;
  }
</style>
