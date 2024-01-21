* Power Dissipation
* Low Power Design
	* Dynamic 
		* 進行開關操作時消耗的功率
		* **clock gating** 關掉CLK
		* DVFS (Dynamic Voltage Frequency Scaling)
		* avoid slow-rising/falling
	* Static
		* 靜態狀態下消耗的功率
		* **power gating** 關閉電源
		* raise Vt (body effect) -> back-bias
* To Reduce Leakage
	* increase Vt
	* increase Vs
	* decrease Vb