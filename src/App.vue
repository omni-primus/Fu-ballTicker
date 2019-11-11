<template>
  <div id="app">
    <div id="nav">
      <a href="javascript:void(0);" class="nav-icon" onclick="shownav()">
        <i class="fa fa-bars" aria-hidden="true"></i>
      </a>
      <div id="links" style="display: block;">
        <router-link class="test" to="/">Home</router-link> |
        <router-link class="test" to="/about">About</router-link> |
        <router-link class="test" to="/Mannschaft">Mannschaft</router-link>
      </div>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  overflow: hidden;
  background-color: rgb(9, 87, 2);
  width: 100%;
  position: fixed;
  z-index: 10000;
  top: 0;
  display: block;
  a {
    float: left;
    display: block;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    font-size: 17px;
    color: #293038;
    &.router-link-exact-active {
      color: #11ca30;
    }
  }
  #links {
    position: relative;
  }
  #links a {
    width: 100%;
    color: black;
  }
}
</style>

<style scoped>
.home {
  color: #000;
  margin-top: 100px;
}
.mannschaft {
  color: #000;
  height: 100px;
  background-color: #20d164;
  margin-top: 100px;
}
</style>

<script>
  function shownav() {
    var x = document.getElementById("links");
    if(x.style.display === "block"){
      x.style.display = "none";
    }else{
      x.style.display = "block";
    }
  }
</script>
