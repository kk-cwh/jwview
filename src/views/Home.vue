
<template>
  <div>
    <!-- <img src="./assets/logo.png"> -->
    <!-- <Rating :grade="2" :maxStars="5" :hasCounter="true"/>-->
    <!-- <HelloWorld></HelloWorld> -->
    <Page :total="total" :page_size="pageSize" @on-change="changeSm"></Page>
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
      total: 1000,
      pageSize: 8,
      grade: 2
    }
  },
  watch: {
    grade: function (val, oldVal) {
      console.log('new: %s, old: %s', val, oldVal)
    }
  },
  methods: {
    changeSm (page) {
      console.log('page', page)
    }
  }
}
</script>

<style>

</style>
