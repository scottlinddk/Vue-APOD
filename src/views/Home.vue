<template>
  <div class="home">


  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Home',
  components: {

  },
  data() {
    return {
      api: 'https://api.nasa.gov/planetary/apod?api_key=',
      token: process.env.VUE_APP_API_KEY,
    }
  },
  created: {

  }
}
</script>
