* Latch: level sensitive
* Flip-Flop: edge trigger (latch* 2 + complementary clock)
* Time Constraint
	* **setup time**
		* the minimum time data must be stable **before** the clock's active edge for reliable sampling.
		* if violated,** use pipeline to reduce the critical path**
	* **hold time**
		* the minimum time data must remain stable **after** the clock's active edge.
		* if violated, **add buffers**
* Time borrowing
* Two-Phase Clocking
* Clock Skew