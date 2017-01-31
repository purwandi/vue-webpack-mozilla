<template>

</template>

<script>
export default {
  name: 'Product',
  props: {
    quantity,
    product: {
      type: Object,
      required: true
    }
  }
}
</script>
