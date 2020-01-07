<template>
  <div class="Home">
    <h1>Fußball Ticker App</h1>
    <div v-if="teamcheck()" id="selection">
      <Checkboxen></Checkboxen>
    </div>
    <div v-else id="div-main">
      <div id="matchresult">
        <table id="match">
          <thead>
            <tr>
              <th>Team 1</th>
              <th>Score</th>
              <th>Team 2</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="team in test" :key="team">
              <td>{{ team.team1 }}</td>
              <td>{{ team.tore1 }}:{{ team.tore2 }}</td>
              <td>{{ team.team2 }}</td>
            </tr>
          </tbody>
        </table>
        <button @click="getData">RAUS</button>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Checkboxen from "@/components/checkboxen.vue";

export default {
  name: "Home",
  components: {
    Checkboxen
  },
  data() {
    return {
      spieltag: [
        {
          team1: "FC Bayern München",
          team2: "FC Schalke 04",
          tore1: 100,
          tore2: 0
        },
        {
          team1: "FC Bayern München",
          team2: "Werder Bremen",
          tore1: 4,
          tore2: 0
        },
        {
          team1: "FC Bayern München",
          team2: "RB Leipzig",
          tore1: 0,
          tore2: 2
        },
        {
          team1: "FC Bayern München",
          team2: "Borussia Dortmund",
          tore1: 2,
          tore2: 2
        },
        {
          team1: "FC Schalke 04",
          team2: "RB Leipzig",
          tore1: 0,
          tore2: 50
        },
        {
          team1: "FC Schalke 04",
          team2: "Werder Bremen",
          tore1: 0,
          tore2: 5
        },
        {
          team1: "FC Schalke 04",
          team2: "Borussia Dortmund",
          tore1: 0,
          tore2: 54
        },
        {
          team1: "RB Leipzig",
          team2: "Werder Bremen",
          tore1: 4,
          tore2: 0
        },
        {
          team1: "RB Leipzig",
          team2: "Borussia Dortmund",
          tore1: 6,
          tore2: 4
        },
        {
          team1: "Borussia Dortmund",
          team2: "Werder Bremen",
          tore1: 5,
          tore2: 1
        }
      ],
      wahl: [],
      test: []
    };
  },
  mounted() {
    if (localStorage.getItem("chosen")) {
      this.wahl = JSON.parse(localStorage.getItem("chosen"));
    }
  },
  methods: {
    teamcheck: function() {
      let x1 = localStorage.getItem("chosen");
      if (x1 == null) {
        return true;
      } else {
        return false;
      }
    },
    getData: function() {
      this.wahl.push(localStorage.getItem("chosen"));
      for (let i = 0; i < this.spieltag.length; i++) {
        for (let j = 0; j < this.wahl.length; j++) {
          let temp = 0;
          if (
            this.spieltag[i].team1 == this.wahl[j] ||
            this.spieltag[i].team2 == this.wahl[j]
          ) {
            for (let k = 0; k < this.test.length; k++) {
              if (this.test[k] == this.spieltag[i]) temp++;
            }
            if (temp == 0) this.test.push(this.spieltag[i]);
          }
        }
      }
    }
  }
};
</script>
