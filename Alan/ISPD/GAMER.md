* Previous Works
	* FastRoute 2.0: monotonic routing
	* bounded-length maze routing
	* SPRoute: routing in the same region (if enough resources)
	* NCTU-GR 2.0: route in overlapping bounding boxes simultaneously, but avoid racing situation
	* use GPUs on A* algorithm: 3x speedup but quality degrade
* Proposed Work
	* **sweep operation**
	* two massively parallel algorithms
* Highly Parallel Maze Routing
	* Sweep: four sweeps can find the shortest path
	* Formulation
	* Parallelization with condition partial sum
	* reformulation and work-efficient algorithm