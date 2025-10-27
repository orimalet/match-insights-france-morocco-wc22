# France vs Morocco — Shot Map & Cumulative xG (World Cup 2022)

An exploratory match analysis of France vs Morocco using StatsBomb Open Data. The notebook builds:

**1.** a **shot map** on a full pitch (size and opacity by xG, colour by team, goals highlighted), and

**2.** a **cumulative xG timeline** with goal annotations (minute + scorer), giving an at a glance view of momentum and chance quality.

## What’s included

- **Data source:** statsbombpy (Open Data).

- **Match selection:** World Cup 2022, **match_id = 3869552** (France vs Morocco).

- **Shot map:** plots all shots with:

  - circle radius ∝ √xG

  - colour by team (France / Morocco)

  - higher opacity for goals

- **Cumulative xG chart:** step plot of xG over time for each team, with goal markers and text annotations.

- **Quick totals:** computes and displays each team’s total xG in the chart legend.

## Stack

- ```python``` • ```pandas``` • ```numpy``` • ```matplotlib``` • ```seaborn```

- ```statsbombpy``` for competitions/matches/events

- ```FCPython``` (utility) for drawing the pitch (```createPitch```)

## How to run
```
# (optional) create a virtual environment
python -m venv .venv
# Windows: .venv\Scripts\activate
source .venv/bin/activate

pip install pandas numpy matplotlib seaborn statsbombpy

# If you don’t already have it, add the FCPython pitch helper:
# Option A: place FCPython.py (with createPitch) alongside the notebook
# Option B: replace createPitch with your own pitch drawing code

# Open the notebook
jupyter notebook France_vs_Morocco.ipynb
```
## Notebook flow

**1. Load competitions & matches** → filter to FIFA World Cup 2022.

**2. Select match** (```match_id = 3869552```).

**3. Pull events** → filter ```type == 'Shot'```.

**4. Shot map →** draw pitch; plot shots with size by shot_statsbomb_xg, highlight goals.

**5. xG timeline** → build cumulative xG per team; annotate goals (minute + player).

**6. Summary** → total xG for each team displayed in the legend.

## Adapting to another match

- Change the ```match_id``` passed to ```sb.events(match_id=...)```.

- (Optional) Re-derive ```home_team/away_team``` labels from the matches table for dynamic titles.

## Why it’s useful (sports analytics angle)

- **Contextual shot quality:** xG conveys chance quality beyond raw shot counts.

- **Game state & momentum:** cumulative xG reveals which team created better chances and when.

- **Scouting/Reporting:** clean visuals suitable for quick post match reports or analyst decks.
