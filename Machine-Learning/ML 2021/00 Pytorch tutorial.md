
* code explaination
	* `a.grad.zero_()`：在每個迭代步驟的開始，將 `a` 的梯度（`a.grad`）歸零。
	* `with torch.no_grad():`：這是一個上下文管理器，用於指示 PyTorch 不要跟踪梯度變化。