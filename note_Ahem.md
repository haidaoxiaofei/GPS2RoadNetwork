## Note on <Constructing Street Networks from GPS Trajectories>

### Key Point

* Incremental Map Update

* The algo contains 3 steps:

1. Compute matched and unmatched portions of an input trajectory.

- for each traj segment(two consecutive gps), mark matched if one road link is epsilon-near(dist less than epsilon), mark unmatched otherwise.

2. Add unmatched portion as an edge in the graph

3. Compress the complexity of matched portion.

- add minimum new link to construct the roadnet
