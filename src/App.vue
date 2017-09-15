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
    background: $white url("./assets/background.png");
    font-family: 'Open Sans', sans-serif;
    color: $black;
  }
</style>
