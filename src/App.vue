<template>
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav> -->

  <div class="app-container p-rel">

    <div class="p-abs img-vs">
      <img
        width="200"
        src="https://upload.wikimedia.org/wikipedia/commons/7/70/Street_Fighter_VS_logo.png"
        alt=""
      />
    </div>
    <router-view />
  </div>
</template>

<script>
import json from '../public/static/config.json'
export default ({
  mounted() {
    console.log(json);
  },

})
</script>


<style>
.app-container {
  min-width: 100vw;
  min-height: 100vh;

}
.img-vs {
    top: 60%;
    left: 50%;
    -webkit-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
    z-index: 10 !important;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  background-image: url("https://lienquan.garena.vn/asset/images/bg-down.jpg");
  background-size: contain;
  min-height: 100vh;
}
body {
  margin: 0;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
.p-rel {
  position: relative;
}

.p-abs {
  position: absolute;
}
</style>
