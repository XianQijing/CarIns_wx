<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
* {padding: 0;margin: 0;}
html {
  height: 100%;
  font-size: 26.7vw;
  background: #f2f2f2;
}
body {
  height: 100%;
}
#app {
  height: 100%;
  font-size: 0.16rem;
  max-width: 650px;
  margin: 0 auto;
}
input::-webkit-input-placeholder {
  color: #999;
}
input:-moz-placeholder {
  color: #999;
}
input::-moz-placeholder {
  color: #999;
}
input:-ms-input-placeholder {
  color: #999;
}
.van-button {
  background: #4B86FE;
  color: #fff;
  width: 3rem;
}
@media screen and (min-width: 760px){
  html {
    font-size: 13.33333vw;
  }
}
@media screen and (min-width: 1025px){
  html {
    font-size: 6.66666vw;
  }
}
</style>
