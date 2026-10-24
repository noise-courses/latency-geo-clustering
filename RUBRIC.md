# Grading rubric — Assignment 4: Spatial Clustering of Internet Measurements

**10 points, graded for completion.** As with the earlier assignments, if the
notebook runs end to end and each part does what it asks, you get full credit.
Whether your cluster boundaries look "right" is *not* graded; a working
pipeline with a defensible written comparison is 10/10.

| # | Item | Pts |
|---|---|---|
| **Part 1 — Spatial interpolation** | | **5** |
| 1.1 | Load `Chicago_speedtests.csv` and project it to a metric CRS (EPSG:32616) so distances are in meters | 1 |
| 1.2a | Implement `generate_grid_points` and generate the grid at a 200 m separation | 1 |
| 1.2b | **Plot** the grid points on the Chicago city boundary | 1 |
| 1.3a | Implement `idw` from scratch following the formula in the notebook | 1 |
| 1.3b | Use `idw` with `power=2` to estimate latency at every grid point | 1 |
| **Part 2 — Hexagon overlay** | | **1** |
| 2 | Complete `hexbin`: assign an H3 `hex_id` at `resolution=8` to each grid point and produce the GeoDataFrame with hexagon boundaries | 1 |
| **Part 3 — Spatial clustering** | | **4** |
| 3.1 | Choose an aggregation function (mean, median, percentile, ...) and compute it per hexagon, **with a written justification** for the choice | 1 |
| 3.2a | Run SKATER with `floor=50` for `n_clusters` from 2 to 11 and plot the clusters for the sweep | 1 |
| 3.2b | **Answer in a markdown cell**: beyond what value of `n_clusters` does the clustering stop changing? | 1 |
| 3.2c | Implement `cluster_kmeans`, plot it with the same `n_clusters`, and **write the comparison** with SKATER (spatial contiguity, geographic patterns) | 1 |

## Requirements that gate the score

- **The notebook must run.** Submit it *executed* (outputs saved). A notebook
  with error tracebacks in the cells that implement graded items, or with no
  outputs at all, is treated as not running: those items earn 0 until fixed
  and resubmitted.
- **Sub-items are all-or-nothing.** Each row is 1 point if done in good faith,
  0 if absent. There are no half points; "did the thing" is the bar.
- **Written answers count.** Items 3.1, 3.2b, and 3.2c require a few sentences
  of explanation, not just code and plots.
- **Plots are deliverables.** Items 1.2b, 3.2a, and 3.2c are only complete if
  the figure is rendered in the saved outputs.
- **Data.** Both CSVs are in
  [noise-courses/data](https://github.com/noise-courses/data) under
  `latency-geo-clustering/`; the notebook expects that repository cloned at
  `data/`. Copies also ship in this repo's `data/` folder. Paths are not
  graded.
- **AI use.** Encouraged, but acknowledge it in the notebook and be ready to
  explain your code. Not acknowledging AI use does not cost points on this
  assignment, but see the syllabus on assessment of understanding.

## Late policy

Due 11:59 p.m. Chicago time on the due date; 96-hour grace balance for the term,
then half credit within one week, then zero. See the syllabus.
