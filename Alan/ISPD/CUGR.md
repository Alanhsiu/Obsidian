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
	* 3D pattern routing
	* multi-level 3D maze routing