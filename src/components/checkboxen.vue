<template>
  <div>
    <details id="bundesliga">
      <summary>Bundesliga</summary>
      <input
        id="FCB"
        type="checkbox"
        name="checkbox"
        value="FC Bayern München"
      />
      <label for="FCB">FC Bayern München</label>
      <br />
      <input
        id="BVB"
        type="checkbox"
        name="checkbox"
        value="Borussia Dortmund"
      />
      <label for="BVB">Borussia Dortmund</label>
      <br />
      <input
        id="UB"
        type="checkbox"
        name="checkbox"
        value="1.FC Union Berlin"
      />
      <label for="UB">1.FC Union Berlin</label>
      <br />
      <input
        id="BMG"
        type="checkbox"
        name="checkbox"
        value="Borussia Mönchen Gladbach"
      />
      <label for="BMG">Borussia Mönchen Gladbach</label>
      <br />
      <input id="RBL" type="checkbox" name="checkbox" value="RB Leipzig" />
      <label for="RBL">RB Leipzig</label>
      <br />
      <input id="SCF" type="checkbox" name="checkbox" value="SC Freiburg" />
      <label for="SCF">SC Freiburg</label>
      <br />
      <input
        id="TSGH"
        type="checkbox"
        name="checkbox"
        value="TSG 1899 Hoffenheim"
      />
      <label for="TSGH">TSG 1899 Hoffenheim</label>
      <br />
      <input
        id="SGEF"
        type="checkbox"
        name="checkbox"
        value="SG Eintracht Frankfurt"
      />
      <label for="SGEF">SG Eintracht Frankfurt</label>
      <br />
      <input id="FCS04" type="checkbox" name="checkbox" value="FC Schalke 04" />
      <label for="FCS04">FC Schalke 04</label>
      <br />
      <input id="BL" type="checkbox" name="checkbox" value="BL" />
      <label for="BL">Bayer 04 Leverkusen</label>
      <br />
      <input id="VFLW" type="checkbox" name="checkbox" value="VFLW" />
      <label for="VFLW">VFL Wolfsburg</label>
      <br />
      <input id="HBSC" type="checkbox" name="checkbox" value="HBSC" />
      <label for="HBSC">Hertha BSC</label>
      <br />
      <input id="FD" type="checkbox" name="checkbox" value="FD" />
      <label for="FD">Fortuna Düsseldorf</label>
      <br />
      <input id="WB" type="checkbox" name="checkbox" value="WB" />
      <label for="WB">Sv Werder Bremen</label>
      <br />
      <input id="FCA" type="checkbox" name="checkbox" value="FCA" />
      <label for="FCA">FC Augsburg</label>
      <br />
      <input id="M05" type="checkbox" name="checkbox" value="M05" />
      <label for="M05">1. FSV Mainz 05</label>
      <br />
      <input id="FCK" type="checkbox" name="checkbox" value="FCK" />
      <label for="FCK">1. FC Köln</label>
      <br />
      <input id="SCP" type="checkbox" name="checkbox" value="SCP" />
      <label for="SCP">SC Paderborn</label>
      <br />
      <button class="button" @click="knopf">
        Trag meine Teams ein
      </button>
    </details>
  </div>
</template>

<script>
export default {
  name: "Checkboxen",
  methods: {
    knopf: function() {
      var checkboxen = document.getElementsByName("checkbox");
      let boxenchecked = [];
      for (let i = 0; i < checkboxen.length; i++) {
        if (checkboxen[i].checked) {
          boxenchecked.push(checkboxen[i].value);
        }
      }
      if (boxenchecked.length != 0) {
        localStorage.setItem("chosen", JSON.stringify(boxenchecked));
        location.reload();
      } else alert("Nichts ausgewählt");
    }
  }
};
</script>

<style scoped>
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
</style>
