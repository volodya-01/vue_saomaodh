<template>
  <div style="width:100%; height:100%;position: absolute; margin:0 auto; z-index:2; overflow:hidden;">
    <div id="myDiv" style="width: 100%;height:0px;z-index:3;position: absolute;top:20px">zhendonghua1</div>
  </div>
</template>

<script>
export default {
  name: "zhendonghua1",
  data() {
    return {};
  },
  mounted() {
    this.saomao();
  },
  methods: {
    saomao() {
      var timer;
      myDiv.style.height = "0";
      cancelAnimationFrame(timer);
      timer = requestAnimationFrame(function fn() {
        if (parseInt(myDiv.style.height) < 1000) {
          myDiv.style.height = parseInt(myDiv.style.height) + 1 + "px";
          var FPS = 100;
          setTimeout(function() {
            requestAnimationFrame(fn);
          }, 3000 / FPS);
        } else {
          cancelAnimationFrame(timer);
          myDiv.style.height = "0";
          setTimeout(function() {
            requestAnimationFrame(fn);
          }, 1800 / FPS);
        }
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#myDiv {
  background: -webkit-linear-gradient(
    rgba(1, 206, 246, 0),
    rgba(1, 206, 246, 0.2)
  ); /* Safari 5.1 - 6.0 */
  background: -o-linear-gradient(
    rgba(1, 206, 246, 0),
    rgba(1, 206, 246, 0.2)
  ); /* Opera 11.1 - 12.0 */
  background: -moz-linear-gradient(
    rgba(1, 206, 246, 0),
    rgba(1, 206, 246, 0.2)
  ); /* Firefox 3.6 - 15 */
  background: linear-gradient(
    rgba(1, 206, 246, 0),
    rgba(1, 206, 246, 0.2)
  ); /* 标准的语法（必须放在最后） */
  border-bottom: 2px solid #00d5ff;
  box-shadow: 0px 2px 1px #01cef6 inset;
}
</style>
