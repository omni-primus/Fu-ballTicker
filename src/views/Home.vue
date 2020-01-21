<template>
  <div class="Home">
    <h1>Fußball Ticker App</h1>
    <div v-if="Seitenindex === 1" id="selection">
      <img id="bund-img" src="images/bundesliga-banner.png" @click="open" />
      <details id="bundesliga">
        <summary></summary>
        <Checkboxen></Checkboxen>
      </details>
      <button class="button-save save" @click="knopf">
        Teams speichern
      </button>
    </div>
    <div v-else-if="Seitenindex === 2" id="div-main">
      <button
        class="button"
        style="float:left;margin-bottom:20px;margin-left:10px;"
        @click="Seitenindex = 3"
      >
        Mannschaftsübersicht
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
              <td class="mitte">{{ team.tore1 }}:{{ team.tore2 }}</td>
              <td>{{ team.team2 }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <div v-if="Seitenindex === 3" id="teaminfo">
      <div style="width:100%;height:10px">
        <button
          class="button"
          style="float:left;margin-bottom:20px;margin-left:10px;"
          @click="Seitenindex = 2"
        >
          Zurück zur Tabelle
        </button>
        <button
          class="button-edit edit"
          style="float:right;margin-bottom:20px;margin-right:10px;"
          @click="Seitenindex = 1"
        >
          Teamauswahl bearbeiten
        </button>
      </div>
      <div style="margin-top:120px;">
        <details v-for="team in TDetails" id="match" :key="team">
          <summary>
            <img
              :src="assetsPath(team.name)"
              style="width:100px; height:100px;"
            />
          </summary>
          <table>
            <tr>
              <td><b>Mannschaft</b></td>
              <td>{{ team.name }}</td>
            </tr>
            <tr>
              <td><b>Trainer</b></td>
              <td>{{ team.trainer }}</td>
            </tr>
            <tr>
              <td><b>Präsident</b></td>
              <td>{{ team.president }}</td>
            </tr>
            <tr>
              <td><b>Stadion</b></td>
              <td>{{ team.stadium }}</td>
            </tr>
            <tr>
              <td><b>Gründungsjahr</b></td>
              <td>{{ team.year }}</td>
            </tr>
            <tr>
              <td><b>Meistertitel</b></td>
              <td>{{ team.title }}</td>
            </tr>
          </table>

          <p style="text-align:left;font-size:20px; padding-left:20px;">
            Letzten 5 Spiele:
          </p>
          <table id="table2">
            <tr
              v-for="match in spieltag
                .filter(
                  spieltag =>
                    team.name === spieltag.team1 || team.name === spieltag.team2
                )
                .slice(0, 5)"
              :key="match"
            >
              <td
                v-if="team.name === match.team1 && match.tore1 < match.tore2"
                class="lose"
              >
                {{ match.team1 }}
              </td>
              <td
                v-else-if="team.name === match.team1 && match.tore1 > match.tore2"
                class="win"
              >
                {{ match.team1 }}
              </td>
              <td
                v-else-if="team.name === match.team1 && match.tore1 === match.tore2"
                class="draw"
              >
                {{ match.team1 }}
              </td>
              <td v-else class="links">
                {{ match.team1 }}
              </td>
              <td class="mitte">{{ match.tore1 }}:{{ match.tore2 }}</td>
              <td
                v-if="team.name === match.team2 && match.tore1 > match.tore2"
                class="lose"
              >
                {{ match.team2 }}
              </td>
              <td
                v-else-if="team.name === match.team2 && match.tore1 < match.tore2"
                class="win"
              >
                {{ match.team2 }}
              </td>
              <td
                v-else-if="team.name === match.team2 && match.tore1 === match.tore2"
                class="draw"
              >
                {{ match.team2 }}
              </td>
              <td v-else class="rechts">
                {{ match.team2 }}
              </td>
            </tr>
          </table>
        </details>
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
      Seitenindex: 1,
      spieltag: [
        {
          team1: "FC Bayern München",
          team2: "FC Schalke 04",
          tore1: 2,
          tore2: 0
        },
        {
          team1: "FC Bayern München",
          team2: "SV Werder Bremen",
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
          team1: "FC Bayern München",
          team2: "1.FC Union Berlin",
          tore1: 2,
          tore2: 2
        },
        {
          team1: "FC Bayern München",
          team2: "Borussia Mönchen Gladbach",
          tore1: 0,
          tore2: 1
        },
        {
          team1: "FC Bayern München",
          team2: "SC Freiburg",
          tore1: 2,
          tore2: 1
        },
        {
          team1: "FC Bayern München",
          team2: "TSG 1899 Hoffenheim",
          tore1: 4,
          tore2: 0
        },
        {
          team1: "FC Bayern München",
          team2: "SG Eintracht Frankfurt",
          tore1: 1,
          tore2: 5
        },
        {
          team1: "FC Bayern München",
          team2: "Bayer 04 Leverkusen",
          tore1: 2,
          tore2: 1
        },
        {
          team1: "FC Bayern München",
          team2: "VFL Wolfsburg",
          tore1: 3,
          tore2: 1
        },
        {
          team1: "FC Bayern München",
          team2: "Hertha BSC",
          tore1: 1,
          tore2: 0
        },
        {
          team1: "FC Bayern München",
          team2: "Fortuna Düsseldorf",
          tore1: 2,
          tore2: 2
        },
        {
          team1: "FC Bayern München",
          team2: "FC Augsburg",
          tore1: 2,
          tore2: 3
        },
        {
          team1: "FC Bayern München",
          team2: "1.FSV Mainz 05",
          tore1: 2,
          tore2: 0
        },
        {
          team1: "FC Bayern München",
          team2: "1.FC Köln",
          tore1: 4,
          tore2: 0
        },
        {
          team1: "FC Bayern München",
          team2: "SC Paderborn",
          tore1: 5,
          tore2: 1
        },
        {
          team1: "FC Schalke 04",
          team2: "RB Leipzig",
          tore1: 0,
          tore2: 5
        },
        {
          team1: "FC Schalke 04",
          team2: "SV Werder Bremen",
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
          team1: "FC Schalke 04",
          team2: "Borussia Mönchen Gladbach",
          tore1: 1,
          tore2: 1
        },
        {
          team1: "FC Schalke 04",
          team2: "SC Freiburg",
          tore1: 3,
          tore2: 0
        },
        {
          team1: "FC Schalke 04",
          team2: "TSG 1899 Hoffenheim",
          tore1: 2,
          tore2: 2
        },
        {
          team1: "FC Schalke 04",
          team2: "SG Eintracht Frankfurt",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "FC Schalke 04",
          team2: "Bayer 04 Leverkusen",
          tore1: 0,
          tore2: 0
        },
        {
          team1: "FC Schalke 04",
          team2: "1.FC Union Berlin",
          tore1: 1,
          tore2: 2
        },
        {
          team1: "FC Schalke 04",
          team2: "VFL Wolfsburg",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "FC Schalke 04",
          team2: "Hertha BSC",
          tore1: 5,
          tore2: 2
        },
        {
          team1: "FC Schalke 04",
          team2: "Fortuna Düsseldorf",
          tore1: 0,
          tore2: 2
        },
        {
          team1: "FC Schalke 04",
          team2: "FC Augsburg",
          tore1: 1,
          tore2: 0
        },
        {
          team1: "FC Schalke 04",
          team2: "1.FSV Mainz 05",
          tore1: 4,
          tore2: 2
        },
        {
          team1: "FC Schalke 04",
          team2: "1.FC Köln",
          tore1: 3,
          tore2: 0
        },
        {
          team1: "FC Schalke 04",
          team2: "SC Paderborn",
          tore1: 4,
          tore2: 1
        },
        {
          team1: "RB Leipzig",
          team2: "SV Werder Bremen",
          tore1: 4,
          tore2: 0
        },
        {
          team1: "RB Leipzig",
          team2: "Borussia Dortmund",
          tore1: 3,
          tore2: 3
        },
        {
          team1: "RB Leipzig",
          team2: "1.FC Union Berlin",
          tore1: 6,
          tore2: 0
        },
        {
          team1: "RB Leipzig",
          team2: "Borussia Mönchen Gladbach",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "RB Leipzig",
          team2: "SC Freiburg",
          tore1: 2,
          tore2: 1
        },
        {
          team1: "RB Leipzig",
          team2: "TSG 1899 Hoffenheim",
          tore1: 3,
          tore2: 0
        },
        {
          team1: "RB Leipzig",
          team2: "SG Eintracht Frankfurt",
          tore1: 4,
          tore2: 1
        },
        {
          team1: "RB Leipzig",
          team2: "VFL Wolfsburg",
          tore1: 4,
          tore2: 2
        },
        {
          team1: "RB Leipzig",
          team2: "Hertha BSC",
          tore1: 3,
          tore2: 1
        },
        {
          team1: "RB Leipzig",
          team2: "Fortuna Düsseldorf",
          tore1: 2,
          tore2: 0
        },
        {
          team1: "RB Leipzig",
          team2: "FC Augsburg",
          tore1: 3,
          tore2: 0
        },
        {
          team1: "RB Leipzig",
          team2: "1.FSV Mainz 05",
          tore1: 4,
          tore2: 1
        },
        {
          team1: "RB Leipzig",
          team2: "1.FC Köln",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "RB Leipzig",
          team2: "SC Paderborn",
          tore1: 6,
          tore2: 2
        },
        {
          team1: "RB Leipzig",
          team2: "Bayer 04 Leverkusen",
          tore1: 4,
          tore2: 3
        },
        {
          team1: "Borussia Dortmund",
          team2: "SV Werder Bremen",
          tore1: 5,
          tore2: 2
        },
        {
          team1: "Borussia Dortmund",
          team2: "1.FC Union Berlin",
          tore1: 4,
          tore2: 1
        },
        {
          team1: "Borussia Dortmund",
          team2: "Borussia Mönchen Gladbach",
          tore1: 3,
          tore2: 0
        },
        {
          team1: "Borussia Dortmund",
          team2: "SC Freiburg",
          tore1: 4,
          tore2: 1
        },
        {
          team1: "Borussia Dortmund",
          team2: "TSG 1899 Hoffenheim",
          tore1: 0,
          tore2: 1
        },
        {
          team1: "Borussia Dortmund",
          team2: "SG Eintracht Frankfurt",
          tore1: 2,
          tore2: 1
        },
        {
          team1: "Borussia Dortmund",
          team2: "Bayer 04 Leverkusen",
          tore1: 3,
          tore2: 1
        },
        {
          team1: "Borussia Dortmund",
          team2: "VFL Wolfsburg",
          tore1: 2,
          tore2: 2
        },
        {
          team1: "Borussia Dortmund",
          team2: "Hertha BSC",
          tore1: 4,
          tore2: 0
        },
        {
          team1: "Borussia Dortmund",
          team2: "Fortuna Düsseldorf",
          tore1: 2,
          tore2: 0
        },
        {
          team1: "Borussia Dortmund",
          team2: "FC Augsburg",
          tore1: 1,
          tore2: 2
        },
        {
          team1: "Borussia Dortmund",
          team2: "1.FSV Mainz 05",
          tore1: 0,
          tore2: 1
        },
        {
          team1: "Borussia Dortmund",
          team2: "1.FC Köln",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "Borussia Dortmund",
          team2: "SC Paderborn",
          tore1: 4,
          tore2: 0
        },
        {
          team1: "SV Werder Bremen",
          team2: "1.FC Union Berlin",
          tore1: 4,
          tore2: 4
        },
        {
          team1: "SV Werder Bremen",
          team2: "Borussia Mönchen Gladbach",
          tore1: 0,
          tore2: 2
        },
        {
          team1: "SV Werder Bremen",
          team2: "SC Freiburg",
          tore1: 1,
          tore2: 1
        },
        {
          team1: "SV Werder Bremen",
          team2: "TSG 1899 Hoffenheim",
          tore1: 0,
          tore2: 3
        },
        {
          team1: "SV Werder Bremen",
          team2: "SG Eintracht Frankfurt",
          tore1: 2,
          tore2: 2
        },
        {
          team1: "SV Werder Bremen",
          team2: "Bayer 04 Leverkusen",
          tore1: 0,
          tore2: 2
        },
        {
          team1: "SV Werder Bremen",
          team2: "VFL Wolfsburg",
          tore1: 0,
          tore2: 2
        },
        {
          team1: "SV Werder Bremen",
          team2: "Hertha BSC",
          tore1: 1,
          tore2: 2
        },
        {
          team1: "SV Werder Bremen",
          team2: "Fortuna Düsseldorf",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "SV Werder Bremen",
          team2: "FC Augsburg",
          tore1: 2,
          tore2: 1
        },
        {
          team1: "SV Werder Bremen",
          team2: "1.FSV Mainz 05",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "SV Werder Bremen",
          team2: "1.FC Köln",
          tore1: 1,
          tore2: 1
        },
        {
          team1: "SV Werder Bremen",
          team2: "SC Paderborn",
          tore1: 0,
          tore2: 0
        },
        {
          team1: "1.FC Union Berlin",
          team2: "Borussia Mönchen Gladbach",
          tore1: 1,
          tore2: 3
        },
        {
          team1: "1.FC Union Berlin",
          team2: "SC Freiburg",
          tore1: 0,
          tore2: 0
        },
        {
          team1: "1.FC Union Berlin",
          team2: "SG Eintracht Frankfurt",
          tore1: 2,
          tore2: 1
        },
        {
          team1: "1.FC Union Berlin",
          team2: "TSG 1899 Hoffenheim",
          tore1: 2,
          tore2: 3
        },
        {
          team1: "1.FC Union Berlin",
          team2: "Bayer 04 Leverkusen",
          tore1: 1,
          tore2: 3
        },
        {
          team1: "1.FC Union Berlin",
          team2: "VFL Wolfsburg",
          tore1: 0,
          tore2: 3
        },
        {
          team1: "1.FC Union Berlin",
          team2: "Hertha BSC",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "1.FC Union Berlin",
          team2: "Fortuna Düsseldorf",
          tore1: 1,
          tore2: 0
        },
        {
          team1: "1.FC Union Berlin",
          team2: "FC Augsburg",
          tore1: 4,
          tore2: 1
        },
        {
          team1: "1.FC Union Berlin",
          team2: "1.FSV Mainz 05",
          tore1: 5,
          tore2: 3
        },
        {
          team1: "1.FC Union Berlin",
          team2: "1.FC Köln",
          tore1: 4,
          tore2: 2
        },
        {
          team1: "1.FC Union Berlin",
          team2: "SC Paderborn",
          tore1: 1,
          tore2: 2
        },
        {
          team1: "Borussia Mönchen Gladbach",
          team2: "SC Freiburg",
          tore1: 4,
          tore2: 0
        },
        {
          team1: "Borussia Mönchen Gladbach",
          team2: "TSG 1899 Hoffenheim",
          tore1: 3,
          tore2: 1
        },
        {
          team1: "Borussia Mönchen Gladbach",
          team2: "SG Eintracht Frankfurt",
          tore1: 5,
          tore2: 3
        },
        {
          team1: "Borussia Mönchen Gladbach",
          team2: "Bayer 04 Leverkusen",
          tore1: 1,
          tore2: 1
        },
        {
          team1: "Borussia Mönchen Gladbach",
          team2: "VFL Wolfsburg",
          tore1: 4,
          tore2: 3
        },
        {
          team1: "Borussia Mönchen Gladbach",
          team2: "Hertha BSC",
          tore1: 1,
          tore2: 2
        },
        {
          team1: "Borussia Mönchen Gladbach",
          team2: "Fortuna Düsseldorf",
          tore1: 0,
          tore2: 1
        },
        {
          team1: "Borussia Mönchen Gladbach",
          team2: "FC Augsburg",
          tore1: 2,
          tore2: 0
        },
        {
          team1: "Borussia Mönchen Gladbach",
          team2: "1.FSV Mainz 05",
          tore1: 2,
          tore2: 0
        },
        {
          team1: "Borussia Mönchen Gladbach",
          team2: "1.FC Köln",
          tore1: 3,
          tore2: 1
        },
        {
          team1: "Borussia Mönchen Gladbach",
          team2: "SC Paderborn",
          tore1: 1,
          tore2: 0
        },
        {
          team1: "SC Freiburg",
          team2: "TSG 1899 Hoffenheim",
          tore1: 1,
          tore2: 3
        },
        {
          team1: "SC Freiburg",
          team2: "SG Eintracht Frankfurt",
          tore1: 1,
          tore2: 1
        },
        {
          team1: "SC Freiburg",
          team2: "Bayer 04 Leverkusen",
          tore1: 2,
          tore2: 3
        },
        {
          team1: "SC Freiburg",
          team2: "VFL Wolfsburg",
          tore1: 0,
          tore2: 2
        },
        {
          team1: "SC Freiburg",
          team2: "Hertha BSC",
          tore1: 1,
          tore2: 1
        },
        {
          team1: "SC Freiburg",
          team2: "Fortuna Düsseldorf",
          tore1: 0,
          tore2: 0
        },
        {
          team1: "SC Freiburg",
          team2: "FC Augsburg",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "SC Freiburg",
          team2: "1.FSV Mainz 05",
          tore1: 2,
          tore2: 1
        },
        {
          team1: "SC Freiburg",
          team2: "1.FC Köln",
          tore1: 3,
          tore2: 1
        },
        {
          team1: "SC Freiburg",
          team2: "SC Paderborn",
          tore1: 2,
          tore2: 2
        },
        {
          team1: "TSG 1899 Hoffenheim",
          team2: "SG Eintracht Frankfurt",
          tore1: 4,
          tore2: 3
        },
        {
          team1: "TSG 1899 Hoffenheim",
          team2: "Bayer 04 Leverkusen",
          tore1: 3,
          tore2: 3
        },
        {
          team1: "TSG 1899 Hoffenheim",
          team2: "VFL Wolfsburg",
          tore1: 4,
          tore2: 4
        },
        {
          team1: "TSG 1899 Hoffenheim",
          team2: "Hertha BSC",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "TSG 1899 Hoffenheim",
          team2: "Fortuna Düsseldorf",
          tore1: 0,
          tore2: 2
        },
        {
          team1: "TSG 1899 Hoffenheim",
          team2: "FC Augsburg",
          tore1: 3,
          tore2: 3
        },
        {
          team1: "TSG 1899 Hoffenheim",
          team2: "1.FSV Mainz 05",
          tore1: 1,
          tore2: 2
        },
        {
          team1: "TSG 1899 Hoffenheim",
          team2: "1.FC Köln",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "TSG 1899 Hoffenheim",
          team2: "SC Paderborn",
          tore1: 4,
          tore2: 0
        },
        {
          team1: "SG Eintracht Frankfurt",
          team2: "Bayer 04 Leverkusen",
          tore1: 0,
          tore2: 1
        },
        {
          team1: "SG Eintracht Frankfurt",
          team2: "VFL Wolfsburg",
          tore1: 0,
          tore2: 3
        },
        {
          team1: "SG Eintracht Frankfurt",
          team2: "Hertha BSC",
          tore1: 2,
          tore2: 0
        },
        {
          team1: "SG Eintracht Frankfurt",
          team2: "Fortuna Düsseldorf",
          tore1: 1,
          tore2: 0
        },
        {
          team1: "SG Eintracht Frankfurt",
          team2: "FC Augsburg",
          tore1: 1,
          tore2: 2
        },
        {
          team1: "SG Eintracht Frankfurt",
          team2: "1.FSV Mainz 05",
          tore1: 0,
          tore2: 3
        },
        {
          team1: "SG Eintracht Frankfurt",
          team2: "1.FC Köln",
          tore1: 3,
          tore2: 0
        },
        {
          team1: "SG Eintracht Frankfurt",
          team2: "SC Paderborn",
          tore1: 0,
          tore2: 0
        },
        {
          team1: "VFL Wolfsburg",
          team2: "Hertha BSC",
          tore1: 4,
          tore2: 0
        },
        {
          team1: "VFL Wolfsburg",
          team2: "Fortuna Düsseldorf",
          tore1: 3,
          tore2: 1
        },
        {
          team1: "VFL Wolfsburg",
          team2: "FC Augsburg",
          tore1: 2,
          tore2: 0
        },
        {
          team1: "VFL Wolfsburg",
          team2: "1.FSV Mainz 05",
          tore1: 1,
          tore2: 2
        },
        {
          team1: "VFL Wolfsburg",
          team2: "1.FC Köln",
          tore1: 3,
          tore2: 1
        },
        {
          team1: "VFL Wolfsburg",
          team2: "SC Paderborn",
          tore1: 2,
          tore2: 0
        },
        {
          team1: "Hertha BSC",
          team2: "Fortuna Düsseldorf",
          tore1: 2,
          tore2: 2
        },
        {
          team1: "Hertha BSC",
          team2: "FC Augsburg",
          tore1: 1,
          tore2: 2
        },
        {
          team1: "Hertha BSC",
          team2: "1.FSV Mainz 05",
          tore1: 2,
          tore2: 1
        },
        {
          team1: "Hertha BSC",
          team2: "1.FC Köln",
          tore1: 3,
          tore2: 0
        },
        {
          team1: "Hertha BSC",
          team2: "SC Paderborn",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "Fortuna Düsseldorf",
          team2: "FC Augsburg",
          tore1: 1,
          tore2: 1
        },
        {
          team1: "Fortuna Düsseldorf",
          team2: "1.FSV Mainz 05",
          tore1: 2,
          tore2: 3
        },
        {
          team1: "Fortuna Düsseldorf",
          team2: "1.FC Köln",
          tore1: 0,
          tore2: 1
        },
        {
          team1: "Fortuna Düsseldorf",
          team2: "SC Paderborn",
          tore1: 2,
          tore2: 0
        },
        {
          team1: "FC Augsburg",
          team2: "1.FSV Mainz 05",
          tore1: 3,
          tore2: 3
        },
        {
          team1: "FC Augsburg",
          team2: "1.FC Köln",
          tore1: 2,
          tore2: 1
        },
        {
          team1: "FC Augsburg",
          team2: "SC Paderborn",
          tore1: 2,
          tore2: 0
        },
        {
          team1: "1.FSV Mainz 05",
          team2: "1.FC Köln",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "1.FSV Mainz 05",
          team2: "SC Paderborn",
          tore1: 1,
          tore2: 0
        },
        {
          team1: "1.FC Köln",
          team2: "SC Paderborn",
          tore1: 0,
          tore2: 0
        },
        {
          team1: "Bayer 04 Leverkusen",
          team2: "VFL Wolfsburg",
          tore1: 2,
          tore2: 1
        },
        {
          team1: "Bayer 04 Leverkusen",
          team2: "Hertha BSC",
          tore1: 3,
          tore2: 2
        },
        {
          team1: "Bayer 04 Leverkusen",
          team2: "Fortuna Düsseldorf",
          tore1: 2,
          tore2: 0
        },
        {
          team1: "Bayer 04 Leverkusen",
          team2: "FC Augsburg",
          tore1: 0,
          tore2: 1
        },
        {
          team1: "Bayer 04 Leverkusen",
          team2: "1.FSV Mainz 05",
          tore1: 1,
          tore2: 1
        },
        {
          team1: "Bayer 04 Leverkusen",
          team2: "1.FC Köln",
          tore1: 4,
          tore2: 3
        },
        {
          team1: "Bayer 04 Leverkusen",
          team2: "SC Paderborn",
          tore1: 6,
          tore2: 1
        }
      ],
      MDetails: [
        {
          name: "FC Bayern München",
          year: 1900,
          president: "Herbert Hainer",
          trainer: "Hansi Flick",
          stadium: "Allianz Arena",
          title: 29
        },
        {
          name: "Borussia Dortmund",
          year: 1909,
          president: "Reinhard Rauball",
          trainer: "Lucien Favre",
          stadium: "Signal Iduna Park",
          title: 8
        },
        {
          name: "1.FC Union Berlin",
          year: 1966,
          president: "Dirk Zingler",
          trainer: "Urs Fischer",
          stadium: "Stadion an der alten Försterei",
          title: 0
        },
        {
          name: "Borussia Mönchen Gladbach",
          year: 1900,
          president: "Rolf Koenigs",
          trainer: "Marco Rose",
          stadium: "Borussia Park",
          title: 5
        },
        {
          name: "RB Leipzig",
          year: 2009,
          president: "Oliver Mintzlaff",
          trainer: "Julian Nagelsmann",
          stadium: "Red Bull Arena",
          title: 0
        },
        {
          name: "SC Freiburg",
          year: 1904,
          president: "Unknown",
          trainer: "Christian Streich",
          stadium: "Schwarzwald-Stadion",
          title: 0
        },
        {
          name: "TSG 1899 Hoffenheim",
          year: 1899,
          president: "Peter Hofmann",
          trainer: "Alfred Schreuder",
          stadium: "Prezero-Arena",
          title: 0
        },
        {
          name: "SG Eintracht Frankfurt",
          year: 1899,
          president: "Peter Fischer",
          trainer: "Adi Hütter",
          stadium: "Commerzbank Arena",
          title: 1
        },
        {
          name: "FC Schalke 04",
          year: 1904,
          president: "Unknown",
          trainer: "David Wagner",
          stadium: "Veltins-Arena",
          title: 1
        },
        {
          name: "Bayer 04 Leverkusen",
          year: 1904,
          president: "Fernando Carro",
          trainer: "Peter Bosz",
          stadium: "BayArena",
          title: 0
        },
        {
          name: "VFL Wolfsburg",
          year: 1945,
          president: "Michael Meeske",
          trainer: "Oliver Glasner",
          stadium: "Volkswagen Arena",
          title: 1
        },
        {
          name: "Hertha BSC",
          year: 1892,
          president: "Michael Preetz",
          trainer: "Jürgen Klinsmann",
          stadium: "Olympiastadion Berlin",
          title: 2
        },
        {
          name: "Fortuna Düsseldorf",
          year: 1895,
          president: "Thomas Röttgermann",
          trainer: "Friedhelm Funkel",
          stadium: "Merkur Spiel-Arena",
          title: 1
        },
        {
          name: "SV Werder Bremen",
          year: 1899,
          president: "Hubert Hess-Grunewald",
          trainer: "Florian Kohfeldt",
          stadium: "Weserstadion",
          title: 4
        },
        {
          name: "FC Augsburg",
          year: 1907,
          president: "Klaus Hofmann",
          trainer: "Martin Schmidt",
          stadium: "WWK Arena",
          title: 0
        },
        {
          name: "1.FSV Mainz 05",
          year: 1905,
          president: "Stefan Hofmann",
          trainer: "Achim Beierlorer",
          stadium: "Opel Arena",
          title: 0
        },
        {
          name: "1.FC Köln",
          year: 1948,
          president: "Werner Wolf",
          trainer: "Markus Gisdol",
          stadium: "Rheinenergiestadion",
          title: 3
        },
        {
          name: "SC Paderborn",
          year: 1985,
          president: "Elmar Volkmann",
          trainer: "Steffen Baumgart",
          stadium: "Benteler-Arena",
          title: 0
        }
      ],
      wahl: [],
      test: [],
      TDetails: [],
      theme: ""
    };
  },
  mounted() {
    let x1 = localStorage.getItem("chosen");
    if (x1 == null) {
      this.Seitenindex = 1;
    } else {
      this.Seitenindex = 2;
      this.getData();
    }
  },
  methods: {
    getData: function() {
      this.wahl = JSON.parse(localStorage.getItem("chosen")); //Teams aus Localstorage in wahl
      for (let i = 0; i < this.spieltag.length; i++) {
        //Spieltag durchsuchen
        for (let j = 0; j < this.wahl.length; j++) {
          //ausgesuchte Teams durchsuchen
          let temp = false; //Variable für Datensatz gefunden
          if (
            this.spieltag[i].team1 == this.wahl[j] ||
            this.spieltag[i].team2 == this.wahl[j] //Team an Stelle 1 oder 2?
          ) {
            for (let k = 0; k < this.test.length; k++) {
              if (this.test[k] == this.spieltag[i]) temp = true; //Wenn Spiel schon vorhanden
            }
            if (temp == false) this.test.push(this.spieltag[i]); //Wenn spiel nicht vorhanden in test pushen
          }
        }
      }
      for (let j = 0; j < this.wahl.length; j++) {
        for (let l = 0; l < this.MDetails.length; l++) {
          //Ausgesuchte Mannschaftsdetails in TDetails kopieren
          if (this.wahl[j] == this.MDetails[l].name)
            this.TDetails.push(this.MDetails[l]);
        }
      }
    },
    knopf: function() {
      var checkboxen = document.getElementsByName("checkbox");
      let boxenchecked = [];
      this.test = []; //eventuellen früheren Inhalt löschen
      this.TDetails = [];
      for (let i = 0; i < checkboxen.length; i++) {
        if (checkboxen[i].checked) {
          boxenchecked.push(checkboxen[i].value);
        }
      }
      this.Seitenindex = 2;
      if (boxenchecked.length != 0) {
        localStorage.setItem("chosen", JSON.stringify(boxenchecked));
      } else localStorage.removeItem("chosen");
      setTimeout(5000);
      this.getData();
    },
    open: function() {
      if (document.getElementById("bundesliga").open == false)
        document.getElementById("bundesliga").open = true;
      else document.getElementById("bundesliga").open = false;
    },
    assetsPath: function(file) {
      return "images/" + file + ".png";
    }
  }
};
</script>
<style>
body {
  background: #000;
  background-image: url("Bg-Image.jpg");
  background-image: url("Bg-Image.jpg");
  background-repeat: no-repeat;
  background-size: 100%;
}
details summary::-webkit-details-marker {
  display: none;
}
summary {
  background-color:rgba(0, 0, 0, 0);
}
#bund-img {
  width: 100%;
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
  background-color: #006d0f;
  transform: scale(1.05, 1.05);
  -webkit-transform: scale(1.05, 1.05);
  -moz-transform: scale(1.05, 1.05);
}

.button-edit {
  background-color: rgb(49, 49, 49);
  border: none;
  color: white;
  padding: 16px 32px;
  white-space: nowrap;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  -webkit-transition-duration: 0.4s; /* Safari */
  transition-duration: 0.4s;
  cursor: pointer;
  border-radius: 10px 10px;
}

.button-save {
  background-color: rgb(49, 49, 49);
  border: none;
  color: white;
  padding: 16px 32px;
  white-space: nowrap;
  text-align: center;
  margin-top: 300px;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  -webkit-transition-duration: 0.4s; /* Safari */
  transition-duration: 0.4s;
  cursor: pointer;
  border-radius: 10px 10px;
}

.button-save:hover {
  background-color: #4caf50;
  color: white;
}

.button-edit:hover {
  background-color: #4caf50;
  color: white;
}

.edit:before {
  content: "\270E";
}

.save:before {
  content: "\2714";
}

table {
  margin-left: auto;
  margin-right: auto;
  text-align: left;
}

td {
  text-align: left;
  height: 50px;
}
td.lose {
  background-color: rgb(202, 43, 43);
  width: 40%;
}
td.win {
  background-color: rgb(53, 230, 68);
  width: 40%;
}
td.draw {
  background-color: rgb(151, 151, 151);
  width: 40%;
}
#table2 td.links {
  width: 45%;
}
#table2 td.rechts {
  width: 45%;
}
#table2 td.mitte {
  width: 10%;
}
</style>
