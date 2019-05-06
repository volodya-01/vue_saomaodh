<template>
  <div>
    <div id="myDiv" style="width: 100%;height:0px;z-index:3;position: absolute;top:-10px;line-height:60px">requestanimationframe</div>
  </div>
</template>
<script>
export default {
  name: "requestanimationframe",
  data() {
    return {};
  },
  mounted() {
    /* 指定FPS帧频，requestAnimationFrame播放动画开始
      自行控制时间跨度，针对低版本浏览器再优化：
如果浏览器没有requestAnimationFrame函数，实际底层还只能用setTimeout模拟，那么可以再改进一下。
 */
    var that = this;
    var fps = 30;
    var now;
    var then = Date.now();
    var interval = 1000 / fps;
    var delta;
    window.requestAnimationFrame =
      window.requestAnimationFrame ||
      window.mozRequestAnimationFrame ||
      window.webkitRequestAnimationFrame ||
      window.msRequestAnimationFrame;
    function tick() {
      if (window.requestAnimationFrame) {
        requestAnimationFrame(tick);
        now = Date.now();
        delta = now - then;
        if (delta > interval) {
          // 这里不能简单then=now，否则还会出现上边简单做法的细微时间差问题。例如fps=10，每帧100ms，而现在每16ms（60fps）执行一次draw。16*7=112>100，需要7次才实际绘制一次。这个情况下，实际10帧需要112*10=1120ms>1000ms才绘制完成。
          then = now - (delta % interval);
          that.draw(); 
        }
      } else {
        setTimeout(tick, interval);
        that.draw();
      }
    }
    tick();
    /* 指定FPS帧频，requestAnimationFrame播放动画结束 */
  },
  methods: {
    draw() {
      if (parseInt(document.getElementById("myDiv").style.height) < 900) {
        document.getElementById("myDiv").style.height =
          parseInt(document.getElementById("myDiv").style.height) + 3 + "px";
      } else {
        document.getElementById("myDiv").style.height = "0";
      }
    }
  }
};
</script>
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
  ); 
  border-bottom: 2px solid #00d5ff;
  box-shadow: 0px 2px 1px #01cef6 inset;
}
</style>


