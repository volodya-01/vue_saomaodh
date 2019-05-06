<template>
  <div class="hello">
    <requestanimationframe/>
 <!--    <zhendonghua1/> -->
  </div>
</template>

<script>
import requestanimationframe from '@/components/requestanimationframe'
import zhendonghua1 from '@/components/zhendonghua1'
export default {
  name: "HelloWorld",
  components:{
    requestanimationframe,
    zhendonghua1
  },
  data() {
    return {};
  },

};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
