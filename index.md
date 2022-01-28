---
layout: default
---

# "We play a different game dude!"

Most of the time the dynamic-domeys say this phrase it is referring to something they just don't know is standard,
e.g. standard 3 camp gank timings based on champ and side of the map.

Let's explore some statistics to see how much is true and how much is severe Dunning-Krueger since S5 knowledge no longer applies.

*N.B. Stats are via Riot API data using last two seasons. These stats are up to date as of `1/26/2022`

## Current Status: _Different Game?_

Currently the Cope-Index&trade; is at: `76.789%`
<input type='range' list='tickmarks' disabled value='76.789' /><datalist id='tickmarks'>
  <option value=0 label='Yes!' style='color:green;'></option>
  <option value=1 label='Probably' style='color:greenyellow;'></option>
  <option value=2 label='Maybe?' style='color:yellow;'></option>
  <option value=3 label='Sometimes' style='color:orange;'></option>
  <option value=4 label='Absolutely Coping'></option>
</datalist>

## Key Research Questions:

#### [WHY DIDN'T WE DODGE... MOOOOOT?!](/dodges)
A look at recency bias and which champs are actually bad on their team but good on enemy team. TLDR:
```python
# Top 5 Good Dodges:
[
  {name: 'taric', ally_wr: 0, enemy_wr: 0.8, delta: -0.8},
  {name: 'kennen', ally_wr: 0.3125, enemy_wr: 0.7778, delta: -0.4653},
  {name: 'olaf', ally_wr: 0.5, enemy_wr: 0.9, delta: -0.4},
  {name: 'twisted_fate', ally_wr: 0.2593, enemy_wr: 0.6207, delta: -0.3614},
  {name: 'ryze', ally_wr: 0.3529, enemy_wr: 0.7143, delta: -0.3613}
]
# Full dodge list (<-20% delta, >10 games):
['taric', 'alistar', 'rell', 'kennen', 'olaf', 'twisted_fate', 'ryze', 'kindred', 'zeri', 'master_yi', 'lissandra', 'vex', 'udyr', 'malzahar']

# Cope Dodges (>20% delta, >10 games):
['aurelion_sol', 'taliyah', 'aphelios', 'maokai', 'kalista', 'sejuani', '']

# Just bad champs in your games (<45% WR on both ally and enemy teams):
['kalista', 'illaoi', 'zoe', 'yorick', 'poppy', 'orianna', 'cho`gath', 'shyvana', 'elise', 'lux', 'viego', 'twitch', 'pantheon', 'wukong', 'lillia', 'yummi', 'zyra', 'rumble', 'nidalee', 'gangplank', 'samira', 'syndra', 'qiyana']
```

#### [> Female: 'What's your rank?' > Steve: 'Listen... I have been duoing..' - Who's fault is it really?](/loser)
A look at Dunning-Krueger, victim-blaming, and psychosis spanning the last 7-years. TLDR:
```bash
# The loser in the queue is currently:
YoRHa Destiny#NA1
```

#### [WHY IS SHE HERE DAWG?](/ganks)
A look at "strimmer ganks" and confirmation bias. TLDR:
```
gank_delta is currently 2.3% off average
rating: insignificant

first_enemy_gank_timing is 0.8322s off average
first_ally_gank_timing is -1.5371s off average
```
