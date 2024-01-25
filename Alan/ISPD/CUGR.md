* Previous Works
	* NCTU-GR, NTHU-Route, NTUgr, FastRoute 4.0
		1. Compressing 3D routing space into 2D, fast but low quality.
		2. Initial routing solution: pattern routing or monotonic routing.
		3. maze routing (may rip-up and reroute)
		4. history costs / dynamic programming for layer assignment
	* FGR
		* directly route the nets in 3D
		* discrete Lagrange multipliers
	* GRIP
		* integer linear programming
* Proposed Algorithm
	* detailed-routability-driven 3D global router
		1. **3D pattern routing**
			* multi-pin -> two-pin net
			* L-shape patterns (dynamic programming)
		2. **multi-level 3D maze routing**
			* maze route (coarsen grid graph) -> highest routability
			* fine-grained maze routing -> find lowest cost path
		3. patching
			* add stand-alone route guides
			* improve detailed routability
* Problem Formulation
	* traditional global routing problem + produce a set of connected rectangle guides (detailed routing aware)
* Terminologies
	* Capacity
		* for a wire edge: max num of nets can use
		* for a G-cell: average capacity of two neighbor edges
	* Demand (already used)
		* for a wire edge: sum of (demand by wires) and (demand by vias -> average)
		* for a G-cell: sum of (demand by wires -> average) and (demand by vias)
	* Resource (not used)
		* $r(u, v) = c(u, v) - d(u, v)$
		* $r(u) = c(u) - d(u)$
* Cost Scheme
* Initial Routing (3D Pattern Routing)
	* Pattern Routing Planning
		* FLUTE generate RSMT (get 2-pin nets)
		* edge shifting (alleviate congestion)
		* net order: use DFS and reverse order 
	* Dynamic Programming
		* pattern routing and layer assignment
		* define minimum sub-tree cost $msc(P_i, l)$, $msc(P_i, P_j, l)$
* Multi-level 3D Maze Routing
	* rip-up and reroute (RRR) by maze routing
		1. maze rote planning
			* grid graph coarsening
			* $C_W$ and $C_V$ 
		2. fine-grained maze routing within guides
			* use the cost scheme before
* Postprocessing / Guide Patching
	* Pin Region Patching
	* Long Segment Patching
	* Violation Patching