<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
  export default {
    name: 'app'
  }
</script>

<style lang="scss">
  @import "styles/fonts";
  @import "styles/colors";

  body {
    margin: 0;
    font-family: 'Lato', sans-serif;
    font-weight: 300;
    color: $white;
    background: $white;
  }
</style>
