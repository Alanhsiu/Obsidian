* concept
	* **Forward propagation**: the process of computing predictions using a model
	* **Backward propagation**: the calculation of gradients to update model parameters
	*    ```x = torch.tensor([3.0])  
		y = torch.tensor([18.0])
		a = torch.tensor([1.0], requires_grad=True)  
		loss_func = torch.nn.MSELoss()  
		optimizer = torch.optim.SGD([a], lr=0.01) 
		for _ in range(100):  
			optimizer.zero_grad()  
			loss = loss_func(y, a * x)  -> forward
			loss.backward()  -> backward
			optimizer.step()```
* code explanation
	* `a.grad.zero_()`：在每個迭代步驟的開始，將 `a` 的梯度（`a.grad`）歸零。
	* `with torch.no_grad():`：這是一個上下文管理器，用於指示 PyTorch 不要跟踪梯度變化。
* Ref
	* https://tree.rocks/deep-learning-from-scratch-pytorch-with-regression-5a12546299ea