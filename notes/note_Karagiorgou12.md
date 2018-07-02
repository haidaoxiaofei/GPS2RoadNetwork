## Note on *On vehicle tracking data-based road network generation*

### Key Point

In general, the framework detects turns first, then clusters the detected turns into intersections, finally connects the intersections. The framework has steps as below.

* Turns and Intersections detection

	1. Turning position detection: when a vehicle is turning, its speed reduces and direction changes.
	2. A turn model is built to describe all the possible movement patterns by using direction (0 is east, degrees increase counter-clockwise).
	3. After turn positions of each trajectory is detected, they cluster turn positions into intersections.

* Connect Intersection Nodes

	1. Scan each trajectory to check whether it contains intersections.
	2. Extract subtrajectories of each route for every two succeesive intersections.
	3. Obtain a set of link samples (a subtrajectory connect two intersections).
	4. Link samples can be used to represent the popularity of the link and most importantly to estimate the width of the link.

* Campact Links: In this stage, there are a lot of link samples between two intersections, we need to campact them.

	1. Sort link samples according to their length so as to process longer links first as they are more significant for link construction.
	2. adjust the geometry of links based on the trajectories' geometry.

* Post Processing: a heuristics-based post processing step is used to improve the quality of the road network. Main observation here is that the underlying trajec- tory data is recorded by means of taking position samples at regular time intervals. In the case of turns, this is especially critical in that a position sample might create turn clusters well in advance or after the actual turn and hence introduce additional intersections, which causes a phenomenon called *trangular intersections*. This step is major to detect and remove these "trangular intersections".