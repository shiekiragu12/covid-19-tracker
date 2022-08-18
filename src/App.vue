<script>
import HeaderComponent from "@/components/HeaderComponent.vue";
export default{
  components:{
    HeaderComponent,
  },
}
</script>
<template>
<HeaderComponent/>
  <div class="container">
    <router-view/>
  </div>
</template>

<style lang="scss">

</style>
