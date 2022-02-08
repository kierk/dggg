---
layout: default
---

## Dodges

Total Games Parsed:
`1061` (I only have a dev riot API key so this is limited for now)

### Team Predictor

Enter in comma seperated champs (3 or 4 on your team and 5 on enemy team):

<script defer src="https://cdnjs.cloudflare.com/ajax/libs/fuse.js/3.4.6/fuse.min.js" type="text/javascript"></script>
{%- include champ-data.html -%}
<script>
  function calculateOutcome() {
    const allyTeam = document.getElementById('allies').value.toLowerCase().split(',');
    const enemyTeam = document.getElementById('enemies').value.toLowerCase().split(',');
    let allyWR = 0;
    let enemyWR = 0;
    let wrAvg = 0;
    let allWRs = [];
    const options = {
      keys: ['name']
    }
    const justNames = Object.entries(champsData[0]).map((champData) => {
      let newObj = champData[1];
      newObj['name'] = champData[0];
      return newObj;
    });
    const fuse = new Fuse(justNames, options);
    if (allyTeam[0] != '') {
      allyTeam.forEach((champName) => {
        console.log(champName);
        const searchItem = fuse.search(champName);
        if (searchItem.length > 0) {
          console.log('Result:');
          console.log(searchItem[0]);
          let winRate = 0
          winRate = searchItem[0].awin / (searchItem[0].awin + searchItem[0].aloss);
          allWRs.push(winRate*100);
        } else {
          wrAvg = 'Not Found: ' + champName;
        }
      });
    }
    if (enemyTeam[0] != '') {
      enemyTeam.forEach((champName) => {
        console.log(champName);
        const searchItem = fuse.search(champName);
        if (searchItem.length > 0) {
          console.log('Result:');
          console.log(searchItem[0]);
          let winRate = 0
          winRate = (1 - searchItem[0].ewin / (searchItem[0].ewin + searchItem[0].eloss));
          allWRs.push(winRate*100);
        } else {
          wrAvg = 'Not Found: ' + champName;
        }
      });
    }

    if (wrAvg == 0) {
      console.log(allWRs);
      wrAvg = allWRs.reduce((a, b) => a + b, 0) / allWRs.length;
    }

    if (wrAvg < 35) {
      document.getElementById("expectedOutcome").style.color = 'red';
    } else if (wrAvg < 65) {
      document.getElementById("expectedOutcome").style.color = 'orange';
    } else {
      document.getElementById("expectedOutcome").style.color = 'green';
    }

    if(isNaN(wrAvg)) {
      $('#expectedOutcome').text(wrAvg);
    } else {
      $(document).ready(function() {
        $('#expectedOutcome').text(wrAvg.toPrecision(4) + '%');
      });
    }
  }

</script>
<p><input type="text" id="allies" class="team-builder" placeholder="Ally Champs (comma seperated)" onkeyup="calculateOutcome()"></p>
<p><input type="text" id="enemies" class="team-builder" placeholder="Enemy Champs (comma seperated)" onkeyup="calculateOutcome()"></p>
<p>Predicted chance to win given history:</p>
<p id="expectedOutcome" class="team-output">Enter champs to see win prediction!</p>
<p class="dataTables_placeholder">Screen too small for dodge table. Please use on desktop / larger window.</p>
<table class='display' id='dodgetable' style='background-color:black;'>
<thead>
  <tr>
    <th>Champ</th>
    <th>WR as Ally</th>
    <th>WR as Enemy</th>
    <th>delta</th>
    <th>W/L Ally</th>
    <th>W/L Enemy</th>
  </tr>
</thead>
<tbody>
{%- for champ_data in site.data.champs %}
{%- for champ in champ_data %}
  <tr>
  <td><img class="img-circle-2" src="{{champ.last.img}}" />&nbsp;{{champ.first}}</td>
  {% assign allytotal = champ.last.awin | plus:champ.last.aloss %}
  {% assign allyfloat = allytotal | times:1.0 %}
  {% if allyfloat > 0 %}
    <td>{{champ.last.awin | divided_by:allyfloat | times:100 | round: 2}}%</td>
  {% else %}
    <td>50%</td>
  {% endif %}
  {% assign etotal = champ.last.ewin | plus:champ.last.eloss %}
  {% if etotal > 0 %}
    <td>{{champ.last.ewin | times:1.0 | divided_by:etotal | times:100 | round: 2}}%</td>
  {% else %}
    <td>50%</td>
  {% endif %}
  {% if allytotal > 0 %}
    {% if etotal > 0 %}
      {% assign awr = champ.last.awin | divided_by:allyfloat | times:100 | round: 2 %}
      {% assign ewr = champ.last.ewin | times:1.0 | divided_by:etotal | times:100 | round: 2 %}
      <td>{{ awr | minus:ewr }}%</td>
    {% else %}
      <td>50%</td>
    {% endif %}
  {% else %}
    <td>50%</td>
  {% endif %}
  <td>{{champ.last.awin}}-{{champ.last.aloss}}</td>
  <td>{{champ.last.ewin}}-{{champ.last.eloss}}</td>
  </tr>
{%- endfor %}
{%- endfor %}

</tbody>
</table>
