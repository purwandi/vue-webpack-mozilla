<template>
  <div class="hello">
    Ini test dari sample sample
    {{ message }}
  </div>
</template>

<script>
export default {
  name: 'StartSample',
  data () {
    return {
      message: 'Hello'
    }
  }
}
</script>

<style>
  .hello {
    color: blue;
  }
</style>
