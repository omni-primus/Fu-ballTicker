<template>
  <div class="Home">
    <h1>Fußball Ticker App</h1>
    <div v-if="boolean" id="selection">
      <img id="bund-img" src="images/bundesliga-banner.png" @click="open" />
      <details id="bundesliga">
        <summary></summary>
        <Checkboxen></Checkboxen>
        <button class="button" @click="knopf">
          Trag meine Teams ein
        </button>
      </details>
    </div>
    <div v-else id="div-main">
      <button
        class="button"
        style="float:left;margin-bottom:20px;margin-left:10px;"
        @click="boolean = true"
      >
        Meine Teamselection
      </button>
      <div id="matchresult">
        <table id="match">
          <thead>
            <tr style="background-color: #4A4A4A;">
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
      boolean: true,
      spieltag: [
        {
          team1: "FC Bayern München",
          team2: "FC Schalke 04",
          tore1: 2,
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
          tore2: 5
        },
        {
          team1: "FC Schalke 04",
          team2: "Werder Bremen",
          tore1: 0,
          tore2: 2
        },
        {
          team1: "FC Schalke 04",
          team2: "Borussia Dortmund",
          tore1: 0,
          tore2: 1
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
  methods: {
    /* teamcheck: function() {
      let x1 = localStorage.getItem("chosen");
      if (x1 == null) {
        return true;
      } else {
        return false;
      }
    }, */
    getData: function() {
      if (localStorage.getItem("chosen")) {
        this.wahl = JSON.parse(localStorage.getItem("chosen"));
      }
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
    },
    knopf: function() {
      var checkboxen = document.getElementsByName("checkbox");
      let boxenchecked = [];
      for (let i = 0; i < checkboxen.length; i++) {
        if (checkboxen[i].checked) {
          boxenchecked.push(checkboxen[i].value);
        }
      }
      this.boolean = false;
      if (boxenchecked.length != 0) {
        localStorage.setItem("chosen", JSON.stringify(boxenchecked));
      } else localStorage.removeItem("chosen");
      setTimeout(3000);
      this.getData();
    },
    open: function() {
      if (document.getElementById("bundesliga").open == false)
        document.getElementById("bundesliga").open = true;
      else document.getElementById("bundesliga").open = false;
    }
  }
};
</script>
<style>
body {
  background: #000;
  background-image: url("C:/Users/doa2w/Documents/Uni/PvB/Fu-ballTicker/Bilder/Bg-Image.jpg");
  background-image: url("C:/Users/doa2w/Documents/Uni/PvB/Fu-ballTicker/Bilder/Bg-Image.jpg");
  background-repeat: no-repeat;
  background-size: 100%;
}
details summary::-webkit-details-marker {
  display: none;
}
#bund-img {
  width: 100%;
}
@media (max-width: 920px) {
  body {
    background-size: 920px;
  }
}
</style>
<style scoped>
.button {
  --background: #03c00d;
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
</style>
