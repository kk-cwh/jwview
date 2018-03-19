<template>
<div class="progress-outer">
<div class="progress-enter" :style="percent" v-text="number+'%'">

</div>
</div>
</template>

<script>

export default {
  props: {
    number: {
      type: Number,
      default: 10
    },
    hi: {
      type: Number,
      default: 10
    }},
  data () {
    return {
      percent: {
        width: this.number + '%'
      }
    }
  },
  mounted () {

  },
  methods: {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.progress-outer{
background: #ebebeb;
padding: 1px;
border-radius: 20px;
border: 2px solid #727475;
}
.progress-enter{
background: #3d8ed1;
border-radius: 10px;
height: 1.1em;
text-align: center;
}
</style>
