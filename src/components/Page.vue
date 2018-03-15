<template>
<div class="page">
    <div>
       <span  v-text="p==='next' || p === 'pre' ? '...':p" v-for="(p,index) in pages" :key="index" :class="{bgcol:current==p}" @click="toPage(p)" ref="child" @mouseover="changeOverStyle(p,index)" @mouseout="changeOutStyle(p,index)"></span>
    </div>

</div>
</template>

<script>

export default {
  props: {
    total: {
      type: Number,
      default: 100
    },
    page_size: {
      type: Number,
      default: 10
    }},
  data () {
    return {
      current: 1,
      show_default: 9,
      total_page: 1
    }
  },
  computed: {
    pages () {
      let arr = []
      if (this.show_default < 9) {
        if (this.show_default > 5) {
          if (this.current <= 2) {
            arr = [1, 2, 3, 'next', this.total_page]
          } else if (this.current > 2 && this.current < (this.total_page - 1)) {
            arr = [1, (this.current - 1), this.current, (this.current + 1), 'next', this.total_page]
          } else {
            arr = [1, 'pre', (this.total_page - 3), (this.total_page - 2), (this.total_page - 1), this.total_page]
          }
        } else {
          for (let i = 1; i <= this.show_default; i++) {
            arr.push(i)
          }
        }
      } else {
        if (this.current <= 3) {
          arr = [1, 2, 3, 4, 5, 'next', (this.total_page - 2), (this.total_page - 1), this.total_page]
        } else if (this.current > 3 && this.current < (this.total_page - 2)) {
          arr = [1, 'pre', (this.current - 2), (this.current - 1), this.current, (this.current + 1), (this.current + 2), 'next', this.total_page]
        } else {
          arr = [1, 'pre', (this.total_page - 6), (this.total_page - 5), (this.total_page - 4), (this.total_page - 3), (this.total_page - 2), (this.total_page - 1), this.total_page]
        }
      }

      return arr
    }
  },
  mounted () {
    this.total_page = Math.ceil(this.total / this.page_size)
    this.show_default = this.total_page > this.show_default ? this.show_default : this.total_page
  },
  methods: {
    toPage (page) {
      if (page === 'pre') {
        this.current = this.current - 1
      } else if (page === 'next') {
        this.current = this.current + 1
      } else {
        this.current = page
      }
      this.$emit('on-change', this.current)
    },
    changeOverStyle (page, index) {
      if (page === 'pre') {
        let element = this.$refs.child[index]
        element.innerHTML = '<<'
      }
      if (page === 'next') {
        let element = this.$refs.child[index]
        element.innerHTML = '>>'
      }
    },
    changeOutStyle (page, index) {
      if (page === 'pre') {
        let element = this.$refs.child[index]
        element.innerHTML = '...'
      }
      if (page === 'next') {
        let element = this.$refs.child[index]
        element.innerHTML = '...'
      }
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.page span{
 display: inline-block;
 width: 48px;
 border: 1px solid #DCDDE1;
 border-radius: 3px;
 margin: 2px;
 text-align: center;
 padding: 4px 2px;
}
 span:hover{
  border-color: #2D8BF0;
  color: #2D8BF0;
}
.bgcol{
  background: #2D8BF0;
}

</style>
