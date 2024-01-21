* Verilog 
	* Levels of Abstraction
		* Behavioral 
		* Register Transfer Level (RTL)
		* Structural: gate-level, switch-level circuits.
* STA（靜態時序分析）：評估和分析數位電路或系統在特定時間點的時序性能的過程，通常在設計階段使用。
* DTA（動態時序分析）：分析數位電路或系統在實際運行時的時序行為，考慮到時鐘變化、信號過渡和環境條件等動態因素。
* Multi-cycle path（多周期路徑）：用於處理需要多個時鐘週期的操作。
* False path（假路徑）：用於忽略不需要時序分析的路徑。
* On-Chip Variation (OCV)（或PVT變異）
	* 製程變異
	* 電壓變異
	* 時間變異
* CPPR（Clock Power Planning and Routing）
	* 主要關注時鐘信號的電源規劃和路由。
	* 確保時鐘信號能夠有效地傳遞到整個IC，同時最小化時鐘電源的功耗。
* TCL（Tool Command Language）是一種腳本語言，通常用於自動化軟件工具和應用程式的操作、配置和自動化任務。它提供了一個簡潔的、易於學習和使用的語法，可以用於不同的軟件工具，如EDA（電子設計自動化）、網絡管理工具和其他腳本化任務。