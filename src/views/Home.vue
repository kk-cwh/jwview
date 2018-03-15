
<template>
  <div>
    <!-- <img src="./assets/logo.png"> -->
    <!-- <Rating :grade="2" :maxStars="5" :hasCounter="true"/>-->
    <!-- <HelloWorld></HelloWorld> -->
    <Page></Page>
  </div>
</template>

<script>
import Rating from '@/components/Rating'
import HelloWorld from '@/components/HelloWorld.vue'
import Page from '@/components/Page.vue'

export default {
  name: 'Home',
  components: { Rating, HelloWorld, Page },
  data () {
    return {
      grade: 2
    }
  },
  watch: {
    grade: function (val, oldVal) {
      console.log('new: %s, old: %s', val, oldVal)
    }
  }
}
</script>

<style>

</style>
