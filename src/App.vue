<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/Mannschaft">Mannschaft</router-link>
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
  a {
    font-weight: bold;
    color: #293038;
    &.router-link-exact-active {
      color: #11ca30;
    }
  }
}
</style>

<style scoped>
.home {
  color: #000;
}
.mannschaft {
  color: #000;
  height: 100px;
  background-color: #20d164;
}
</style>
