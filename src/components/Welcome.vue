<template>
  <ul class="content">
    <li id="first-line">{{hello}}. I'm <strong>Steve Krueger.</strong><br/></li>
    <li>I'm a founding partner of <a href="http://thejibe.com" target="_blank">The Jibe</a>, an ecommerce web development agency situated in beautiful Vancouver, Canada.
    </li>
    <li>
      I'm an avid technologist, moonlight as an electronic DJ throughout Vancouver, and own a monochromatic t-shirt collection.<br/>
    </li>
    <li><a href="http://konnection.ca" target="_blank">I occassionally make loud noises.</a></li>
  </ul>

</template>

<script>
  export default {
    name: 'welcome',
    data () {
      return {
        hello: 'Hi'
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>
