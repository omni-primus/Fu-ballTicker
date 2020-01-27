<template>
  <ul class="sidenav">
    <li><a class="active" href="">Ergebnisse</a></li>
    <li><a href="">News</a></li>
    <li><a href="">Mannschaftsübersicht</a></li>
  </ul>
</template>

<script>
export default {
  name: "Nav",
  data() {
    return {};
  }
};
</script>

<style>
ul.sidenav {
  list-style-type: none;
  margin: 0;
  padding: 0;
  background-color: #f1f1f1;
  position: fixed;
  height: 100%;
  overflow: auto;
}

ul.sidenav li a {
  display: block;
  color: #000;
  padding: 8px 16px;
  text-decoration: none;
}

ul.sidenav li a.active {
  background-color: #4caf50;
  color: white;
}

ul.sidenav li a:hover:not(.active) {
  background-color: #555;
  color: white;
}

@media screen and (max-width: 900px) {
  ul.sidenav {
    width: 100%;
    height: auto;
    position: relative;
  }

  ul.sidenav li a {
    float: left;
    padding: 15px;
  }
}

@media screen and (max-width: 400px) {
  ul.sidenav li a {
    text-align: center;
    float: none;
  }
}
</style>
