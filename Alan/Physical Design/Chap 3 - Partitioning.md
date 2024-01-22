* Two issues
	* cut size
	* balanced partitions
* K-L
	* keep partitions balanced
	* minimize cut costs by **swapping vertices**
	* O($rn^3$)
* F-M
	* only **a single vertex** is moved each time
	* can handle unbalanced partitions
	* O(P), P is the total # of terminals
* Multilevel partition
	* Coarsening
	* Uncoarsening
	* hMetis: Multilevel 2-way Partitioner
	* Hyperedge Coarsening/Clustering