<template>
  <div>
    <the-header title="The Learning Resource App"></the-header>
    <the-resource></the-resource>
  </div>
</template>

<script>
  import TheHeader from './components/layouts/TheHeader'
  import TheResource from './components/learning-resources/TheResource'

  export default {
    components: {
      TheHeader,
      TheResource
    },
    
  }
</script>

<style>

  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700;900&display=swap');

  html {
    font-family: 'Roboto', sans-serif;
  }
  
  * {
    box-sizing: border-box;
  }

  body {
    margin: 0;
  }

</style>