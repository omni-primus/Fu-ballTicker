<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <ul id="">
  <li v-for="item in items">
    {{ item.message }}
  </li>
</ul>
  </div>
</template>

<script>
var example1 = new Vue({
  el: "#ergebnisListe",
  data: {
    items:[
      { message: "FC Bayern 2:1 Dortmund" },
      { message: "RB Leipzig 3:2 Gladbach" }
    ]
  }
})
</script>

<script>
export default {
  name: "Start",
  props: {
    msg: { type: String, default: "Test" }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #000;
}
</style>
