<template>
  <div id="app">
    <div>
      <img src="@/img/taxi-icon.png" />
      <div class="title">武汉市出租车时空轨迹分析系统</div>
    </div>
    <web-map />
  </div>
</template>

<script>
import WebMap from "./components/WebMap.vue";

export default {
  name: "App",
  components: { WebMap },
};
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
}
#app {
  display: flex;
  flex-direction: column;
  padding: 0;
  margin: 0;
  width: 100%;
  height: 100%;
}
.title {
  position: fixed;
  top: 0;
  width: 100vw;
  /* height: 40px; */
  z-index: 100;
  font-size: 26px;
  margin: 6px 0 0 50px;
}
img {
  width: 30px;
  height: 30px;
  margin: 8px 10px 0 14px;
}
</style>