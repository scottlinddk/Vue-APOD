<template>
  <div class="relative p-6 flex-auto">
<iframe width="560" height="315"
:src="apodDataObj.url" frameborder="0" 
allowfullscreen></iframe>
  </div>
</template>

<script>
export default {
  name: "AppVideoFrame",
  props: {
    apodDataObj: {
      type: Object,
    },
  }
};
</script>

<style>
</style>