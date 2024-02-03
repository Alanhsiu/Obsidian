* Previous Works
	* Labyrinth: pattern route (L or Z)
	* FastRoute: congestion-driven Steiner tree/edge shifting 
	* FastRoute 2.0: monotonic routing (for 2-pin nets)
	* PathFinder: negotiation-based rip-up and reroute
	* NCTU-GR: history term gradually wears off
	* BOXRouter, SideWinder, GRIP: concurrent routing (use ILP)
	* SPRoute: soft capacity
	* FastGR, Gamer: use GPUs
* Proposed Algorithm
	* **DAG-based generalized pattern routing**
	* use dynamic programming to calculate the cost of a given DAG
	* DAG augmentation algorithm -> Over 99% of nets can be successfully routed without maze routing.
	* new sparse graph maze routing algorithm
* Routing DAG
	1. construct RSMT
	2. DFS construct directed path -> connect the second endpoint to the first endpoint