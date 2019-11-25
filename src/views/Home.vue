<template>
  <div class="home">
    <start msg="Fußball Ticker App" />
    <div id="selection">
      <details v-if="lol()" id="bundesliga">
        <summary>Bundesliga</summary>
        <input id="FCB" type="checkbox" name="FCB" />
        <label for="FCB">1.FC Bayern München</label>
        <br />
        <input id="BVB" type="checkbox" name="BVB" />
        <label for="BVB">Borussia Dortmund</label>
        <br />
        <input id="UB" type="checkbox" name="UB" />
        <label for="UB">1.FC Union Berlin</label>
        <br />
        <input id="BMG" type="checkbox" name="BMG" />
        <label for="BMG">Borussia Mönchen Gladbach</label>
        <br />
        <input id="RBL" type="checkbox" name="RBL" />
        <label for="RBL">RB Leipzig</label>
        <br />
        <input id="SCF" type="checkbox" name="SCF" />
        <label for="SCF">SC Freiburg</label>
        <br />
        <input id="TSGH" type="checkbox" name="TSGH" />
        <label for="TSGH">TSG 1899 Hoffenheim</label>
        <br />
        <input id="SGEF" type="checkbox" name="SGEF" />
        <label for="SGEF">SG Eintracht Frankfurt</label>
        <br />
        <input id="FCS04" type="checkbox" name="FCS04" />
        <label for="FCS04">FC Schalke 04</label>
        <br />
        <input id="BL" type="checkbox" name="BL" />
        <label for="BL">Bayer 04 Leverkusen</label>
        <br />
        <input id="VFLW" type="checkbox" name="VFLW" />
        <label for="VFLW">VFL Wolfsburg</label>
        <br />
        <input id="HBSC" type="checkbox" name="HBSC" />
        <label for="HBSC">Hertha BSC</label>
        <br />
        <input id="FD" type="checkbox" name="FD" />
        <label for="FD">Fortuna Düsseldorf</label>
        <br />
        <input id="WB" type="checkbox" name="WB" />
        <label for="WB">Sv Werder Bremen</label>
        <br />
        <input id="FCA" type="checkbox" name="FCA" />
        <label for="FCA">FC Augsburg</label>
        <br />
        <input id="M05" type="checkbox" name="M05" />
        <label for="M05">1. FSV Mainz 05</label>
        <br />
        <input id="FCK" type="checkbox" name="FCK" />
        <label for="FCK">1. FC Köln</label>
        <br />
        <input id="FCS04" type="checkbox" name="FCS04" />
        <label for="FCS04">FC Schalke 04</label>
        <br />
        <button>Teams bestätigen</button>
      </details>
      <details v-else style="display:none;"></details>
    </div>
  </div>
</template>
<script>
// @ is an alias to /src
import Start from "@/components/start.vue";

export default {
  name: "Home",
  components: {
    Start
  },
  methods: {
    showfirst: function() {
      let erster = document.getElementById("#erster");
      erster.style.display = "";
    },
    GetCookie: function(name) {
      var arg = name + "=";
      var alen = arg.length;
      var clen = document.cookie.length;
      var i = 0;
      while (i < clen) {
        var j = i + alen;
        if (document.cookie.substring(i, j) == arg) return "here";
        i = document.cookie.indexOf(" ", i) + 1;
        if (i == 0) break;
      }
      return null;
    },
    lol: function() {
      let x1 = localStorage.getItem("visit");
      if (x1 == null) {
        localStorage.setItem("visit", "1");
        return false;
      } else {
        return true;
      }
    }
  }
};
</script>
