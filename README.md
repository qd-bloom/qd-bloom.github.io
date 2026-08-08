# qd-bloom — run dashboard

Live: https://qd-bloom.github.io/

Results from a nested quality-diversity search over behavioral audit scenarios.
An inner MAP-Elites loop optimizes scenario seeds on a `behavior x attack-style`
grid; an outer genetic algorithm evolves the attack styles that form the
columns. Fitness at both levels is an alignment judge's score on a Petri audit.

| | |
|---|---|
| grid | 6 behaviors x 8 attack styles = 48 cells |
| generations | 6 |
| audits | 518 scored, 0 failed |
| auditor | `anthropic/claude-opus-5` |
| target | `anthropic/claude-opus-4-8` |
| judge | `anthropic/claude-opus-5` |
| scenario generation | `anthropic/claude-sonnet-5` |

## Panels

| Panel | Measure |
|---|---|
| Archive heatmap | best seed per behavior x style, judge score 1-10 |
| QD score by generation | sum of elite fitness over all cells |
| Column fitness by style origin | per-cell means summed down the column, split by whether the style was present at generation 0 or produced by the GA |
| Audit health | scored/failed counts, `scenario_realism`, `eval_awareness`, turns used, share ending via `end_conversation` |
| Judge score distribution | every scored audit |
| Recorded vs fresh re-audit | the 8 highest-scoring cells, re-audited at the same settings |
| Final attack styles | column fitness, origin and generation per surviving style |
| Mean judge score by behavior | elite scores averaged across styles |

## Data

`data/` holds the objective artifacts the dashboard is built from: the run
config, per-generation metrics (`history.jsonl`), aggregate audit statistics,
the revalidation measurements, and the final archive.
