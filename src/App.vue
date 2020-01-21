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
  color: #fff;
  width: 920px;
  margin-left: auto;
  margin-right: auto;
  background-image: linear-gradient(
    to top,
    rgba(14, 117, 0, 0.3) 20%,
    rgba(0, 0, 0, 0.5) 50%
  );
  height: auto;
  border-radius: 10px 10px;
  padding: 5px;
  padding-bottom: 30px;
}

#div-main {
  /*background-color: rgba(0, 0, 0, 0.5);*/
  width: 100%;
}

#matchresult {
  height: auto;
  text-align: center;
  padding-bottom: 10px;
  padding-top: 10px;
}

table#match {
  width: 80%;
  border-collapse: collapse;
  margin-right: 10%;
  margin-left: 10%;
  font-size: 20px;
  text-align: center;
}
table#table2 {
  width: 80%;
  border-collapse: collapse;
  margin-right: 10%;
  margin-left: 10%;
  font-size: 20px;
}

table#table2 td {
  text-align: center;
  height: 50px;
}
table#match tr:nth-child(even) {
  background-color: #66ff6e;
  color: black;
}
table#match tr {
  background-color: #242424;
  color: white;
}

table#match td {
  text-align: center;
  height: 50px;
  width: 45%;
}
table#match td.mitte {
  text-align: center;
  height: 50px;
  width: 10%;
}
@media (max-width: 920px) {
  #app {
    width: 100%;
  }
  body {
    background-size: 1920px;
  }
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
