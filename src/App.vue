<template>
  <div id="app">
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
.button {
  --background: #275efe;
  color: #fff;
  padding: 16px 32px;
  display: inline-block;
  font-size: 16px;
  margin-top: 30px;
  overflow: hidden;
  text-decoration: none;
  background: var(--background);
  border-radius: 8px;
  -webkit-transition-duration: 0.4s; /* Safari */
  transition-duration: 0.4s;
  cursor: pointer;
}
.button:hover {
  background-color: #4270fa;
  transform: scale(1.05, 1.05);
  -webkit-transform: scale(1.05, 1.05);
  -moz-transform: scale(1.05, 1.05);
}
#div-main {
  background-color: rgba(0, 0, 0, 0.5);
  width: 100%;
}
.matchresult {
  height: auto;
  text-align: center;
}
table.match {
  width: 80%;
  border-collapse: collapse;
  margin-right: 10%;
  margin-left: 10%;
  font-size: 20px;
}
table.match tr:nth-child(even) {background-color: #66ff6e; color: black;}
table.match tr {
  background-color: #242424;
  color: white;
}
td {
  text-align: center;
  width: 33.33333%;
  height: 50px;
}
</style>

<style scoped lang="scss">
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
