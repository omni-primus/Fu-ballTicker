<template>
  <div>
    <label class="container" for="FC Bayern München">
      FC Bayern München
      <input
        id="FC Bayern München"
        type="checkbox"
        name="checkbox"
        value="FC Bayern München"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="Borussia Dortmund">
      Borussia Dortmund
      <input
        id="Borussia Dortmund"
        type="checkbox"
        name="checkbox"
        value="Borussia Dortmund"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="1.FC Union Berlin">
      1.FC Union Berlin
      <input
        id="1.FC Union Berlin"
        type="checkbox"
        name="checkbox"
        value="1.FC Union Berlin"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="Borussia Mönchen Gladbach">
      Borussia Mönchen Gladbach
      <input
        id="Borussia Mönchen Gladbach"
        type="checkbox"
        name="checkbox"
        value="Borussia Mönchen Gladbach"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="RB Leipzig">
      RB Leipzig
      <input
        id="RB Leipzig"
        type="checkbox"
        name="checkbox"
        value="RB Leipzig"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="SC Freiburg">
      SC Freiburg
      <input
        id="SC Freiburg"
        type="checkbox"
        name="checkbox"
        value="SC Freiburg"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="TSG 1899 Hoffenheim">
      TSG 1899 Hoffenheim
      <input
        id="TSG 1899 Hoffenheim"
        type="checkbox"
        name="checkbox"
        value="TSG 1899 Hoffenheim"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="SG Eintracht Frankfurt">
      SG Eintracht Frankfurt
      <input
        id="SG Eintracht Frankfurt"
        type="checkbox"
        name="checkbox"
        value="SG Eintracht Frankfurt"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="FC Schalke 04">
      FC Schalke 04
      <input
        id="FC Schalke 04"
        type="checkbox"
        name="checkbox"
        value="FC Schalke 04"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="Bayer 04 Leverkusen">
      Bayer 04 Leverkusen
      <input
        id="Bayer 04 Leverkusen"
        type="checkbox"
        name="checkbox"
        value="Bayer 04 Leverkusen"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="VFL Wolfsburg">
      VFL Wolfsburg
      <input
        id="VFL Wolfsburg"
        type="checkbox"
        name="checkbox"
        value="VFL Wolfsburg"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="Hertha BSC">
      Hertha BSC
      <input
        id="Hertha BSC"
        type="checkbox"
        name="checkbox"
        value="Hertha BSC"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="Fortuna Düsseldorf">
      Fortuna Düsseldorf
      <input
        id="Fortuna Düsseldorf"
        type="checkbox"
        name="checkbox"
        value="Fortuna Düsseldorf"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="SV Werder Bremen">
      SV Werder Bremen
      <input
        id="SV Werder Bremen"
        type="checkbox"
        name="checkbox"
        value="SV Werder Bremen"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="FC Augsburg">
      FC Augsburg
      <input
        id="FC Augsburg"
        type="checkbox"
        name="checkbox"
        value="FC Augsburg"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="1.FSV Mainz 05">
      1.FSV Mainz 05
      <input
        id="1.FSV Mainz 05"
        type="checkbox"
        name="checkbox"
        value="1.FSV Mainz 05"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="1.FC Köln">
      1.FC Köln
      <input id="1.FC Köln" type="checkbox" name="checkbox" value="1.FC Köln" />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="SC Paderborn">
      SC Paderborn
      <input
        id="SC Paderborn"
        type="checkbox"
        name="checkbox"
        value="SC Paderborn"
      />
      <span class="checkmark"></span>
    </label>
    <button class="button" @click="checkall">Alle auswählen/ entfernen</button>
  </div>
</template>

<script>
export default {
  name: "Checkboxen",
  data() {
    return {
      x1: [],
      x2: []
    };
  },
  mounted() {
    this.checkthebox();
  },
  methods: {
    checkthebox() {
      this.x1 = JSON.parse(localStorage.getItem("chosen"));
      for (let i = 0; i < this.x1.length; i++) {
        let el = document.getElementById(this.x1[i]);
        el.checked = true;
      }
    },
    checkall: function() {
      let el = document.getElementsByName("checkbox");
      for (let j = 0; j < el.length; j++) {
        if (el[j].checked == true) {
          this.x2.push(j);
        }
      }
      if (this.x2.length == 0) {
        for (let i = 0; i < el.length; i++) {
          el[i].checked = true;
        }
      } else {
        for (let i = 0; i < this.x2.length; i++) {
          let wert = this.x2[i];
          el[wert].checked = false;
        }
        this.x2 = [];
      }
    }
  }
};
</script>

<style>
.container {
  display: block;
  position: relative;
  margin-bottom: 0px;
  cursor: pointer;
  font-size: 20px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

.checkmark {
  position: absolute;
  top: 0;
  left: 20%;
  height: 25px;
  width: 25px;
  background-color: #eee;
}

.container:hover input ~ .checkmark {
  background-color: #ccc;
}

.container input:checked ~ .checkmark {
  background-color: #2196f3;
}

.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

.container input:checked ~ .checkmark:after {
  display: block;
}

.container .checkmark:after {
  left: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}

@media (max-width: 385px) {
  .checkmark {
    left: 0px;
  }
}
</style>
