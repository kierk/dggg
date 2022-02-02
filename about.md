---
layout: default
---

## FAQ

#### WHO?

Oh, who am I? Great question! I am kierke, 11+ year veteran of the dgg community, former recurring stream character, boomer, rock climber, unhinged league stat poster in MrMouton's chat. Masters last season, GM this season Copege. Currently, I consider myself a MrMouton community member and a Destiny hate-watcher.

#### Why?

I really don't know. It started as a joke, expecting all the champ winrates to be 50/50, regardless of team, and the gank data to be more or less average. After delving deeper and deeper I don't know what to believe anymore, so I am deferring to numbers from now on and letting other people draw their conclusions out of them.

Example:
>"Twisted Fates on Destiny's team have 18% WR and enemy TFs win 54% with a large sample size.."
>
>Example conclusion 1: Destiny does not know how to play around Twisted Fate's properly and tilts / flames with them on his team.
>
>Example conclusion 2: Destiny is insanely unlucky.
>
>Example conclusion 3: Destiny is secretly inting when TF is on his team to negatively skew the WR on op.gg so TF is played less!
>
>You decide!

#### Where are these stats from?

I am using the riot third party dev API to pull info from `Matches v5` endpoint. I am running those through a python script powered by the Cassiopeia package to produce data for the site.

#### Why doesn't the site update?

I am just serving the site statically from a free pages.dev setup. If interest expands I will hook up an actual webserver / database / start doing more interesting stuff.

#### Is this a meme?

To me, no. But I'm pretty unhinged and I recognize that :^) - help me get better, [patreon.com/dggg](patreon.com/dggg)

#### Planned Features?

Currently on my radar / in development ([patreon.com/dggg](patreon.com/dggg)) sign up to get to vote on next feature):
- [In Progress] Add multi-search widget to dodges page that, given their ally champs and enemy champs would output a predicted win % based on their performance playing with OR against those champs.
- `Snipers` page for the most prolific stream snipers. This would be cool because I use an id that doesn't care about name changes so it would keep up to date based on riot backend id.
  - Could potentially add other popular streamers and their snipers
- Add a non-streamer page where people can look up their summoner name (pending if I can get an upgraded Riot API Key, and some hosting and server maintenance money on [patreon.com/dggg](patreon.com/dggg))
- Graph of WR vs how much time moot spent roaming before 10 or 15 minutes.
- Graph the avg enemy bot gank timings based on champ vs enemy ganks in their games
  - No, I won't do gank frequency because it's too vague, obviously its skewed because they don't understand wave management fundamentals and back timings, not just because they are streamers. I think the first gank timing metric above is more interesting
  - Heatmap of time they spend pushed up vs avg dia+ Tristana's (can't blame the champ)
- Graph of win rate vs number of flame messages Steve sends in first 20 minutes of game (not sure if I can get enough data from API for this)
- ...message me other ideas in dgg or on twitter (sidebar has links)
