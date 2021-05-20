<template>
  <div class="wrapper">
    <h1>您好，欢迎您进入微应用{{ url }}的世界</h1>
  </div>
</template>

<script>

export default {
  components: {},
  data() {
    return {
      url: window.location.href
    }
  },
  computed: {},
  watch: {},
  created() {
    console.log(window.location)
  },
  mounted() {

  },
  methods: {

  }
}
</script>
<style scoped lang='scss'>
/* @import url(); 引入公共css类 */

</style>
