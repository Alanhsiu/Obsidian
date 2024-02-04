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
	1. construct RSMT (FLUTE)
	2. DFS construct directed path -> connect the second endpoint to the first endpoint
* Dynamic Programming-based Vertex Cost Update
	* $mvc(v, k)$ is the minimum routing cost to connect all the upstream pins to the vertex $v$ on layer $k$
	* the minimum routing cost for the whole net is $min[1<=k<=L]  mvc(r, k)$. r is the root vertex, and L is the number of layers.
	* time complexity is $O(L^2|V|)$
* DAG Augmentation for Congestion-Aware Routing
	* create alternative paths for the edge on its two sides
* CUGR 2.0
	* Phase 1: DAG-based pattern routing
	* Phase 1: DAG-based pattern routing with augmentation
	* Phase 3: Sparse graph maze routing