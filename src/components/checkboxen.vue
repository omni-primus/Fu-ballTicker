<template>
  <div>
    <label class="container" for="FCB">
      FC Bayern München
      <input
        id="FCB"
        type="checkbox"
        name="checkbox"
        value="FC Bayern München"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="BVB">
      Borussia Dortmund
      <input
        id="BVB"
        type="checkbox"
        name="checkbox"
        value="Borussia Dortmund"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="UB">
      1.FC Union Berlin
      <input
        id="UB"
        type="checkbox"
        name="checkbox"
        value="1.FC Union Berlin"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="BMG">
      Borussia Mönchen Gladbach
      <input
        id="BMG"
        type="checkbox"
        name="checkbox"
        value="Borussia Mönchen Gladbach"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="RBL">
      RB Leipzig
      <input id="RBL" type="checkbox" name="checkbox" value="RB Leipzig" />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="SCF">
      SC Freiburg
      <input id="SCF" type="checkbox" name="checkbox" value="SC Freiburg" />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="TSGH">
      TSG 1899 Hoffenheim
      <input
        id="TSGH"
        type="checkbox"
        name="checkbox"
        value="TSG 1899 Hoffenheim"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="SGEF">
      SG Eintracht Frankfurt
      <input
        id="SGEF"
        type="checkbox"
        name="checkbox"
        value="SG Eintracht Frankfurt"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="FCS04">
      FC Schalke 04
      <input id="FCS04" type="checkbox" name="checkbox" value="FC Schalke 04" />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="BL">
      Bayer 04 Leverkusen
      <input
        id="BL"
        type="checkbox"
        name="checkbox"
        value="Bayer 04 Leverkusen"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="VFLW">
      VFL Wolfsburg
      <input id="VFLW" type="checkbox" name="checkbox" value="VFL Wolfsburg" />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="HBSC">
      Hertha BSC
      <input id="HBSC" type="checkbox" name="checkbox" value="Hertha BSC" />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="FD">
      Fortuna Düsseldorf
      <input
        id="FD"
        type="checkbox"
        name="checkbox"
        value="Fortuna Düsseldorf"
      />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="WB">
      SV Werder Bremen
      <input id="WB" type="checkbox" name="checkbox" value="Sv Werder Bremen" />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="FCA">
      FC Augsburg
      <input id="FCA" type="checkbox" name="checkbox" value="FC Augsburg" />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="M05">
      1. FSV Mainz 05
      <input id="M05" type="checkbox" name="checkbox" value="1.FSV Mainz 05" />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="FCK">
      1. FC Köln
      <input id="FCK" type="checkbox" name="checkbox" value="1.FC Köln" />
      <span class="checkmark"></span>
    </label>
    <label class="container" for="SCP">
      SC Paderborn
      <input id="SCP" type="checkbox" name="checkbox" value="SC Paderborn" />
      <span class="checkmark"></span>
    </label>
  </div>
</template>

<script>
export default {
  name: "Checkboxen"
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