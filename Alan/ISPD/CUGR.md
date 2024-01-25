* Previous ways
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
* Proposed techs
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