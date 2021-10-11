<template>
  <div>{{ apod }}</div>
</template>

<script>
export default {
  name: 'AppVideo',
  props: {
    apodDataObj: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      apod: this.apodDataObj,
    }
  }
}
</script>

<style>

</style>