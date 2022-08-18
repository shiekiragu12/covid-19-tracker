<template>
<Header class="text-center bg-blue-800 text-white
p-4 mb-10 ">
  <div class="text-3xl md:text-5xl font-bold mb-3
">
    <i class="bi bi-virus"></i> Covid-19 tracker
  </div>
  <p>API by
    <a href="https://covid19api.com" target="_blank"
       class="text-blue-300">Covid19api.com</a></p>
</Header>
</template>

<script>
export default {
  name: 'HeaderComponent',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
