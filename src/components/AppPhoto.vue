<template>
  <div>
    
  </div>



  <p>{{ apiData }}</p>
</template>

<script>
export default {
  name: 'AppPhoto',
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