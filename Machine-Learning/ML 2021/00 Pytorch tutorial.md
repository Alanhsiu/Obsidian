* concept
	* **Forward propagation** is the process of computing predictions using a model, while backward propagation is the calculation of gradients to update model parameters, together forming the training process in deep learning.
* code explanation
	* `a.grad.zero_()`：在每個迭代步驟的開始，將 `a` 的梯度（`a.grad`）歸零。
	* `with torch.no_grad():`：這是一個上下文管理器，用於指示 PyTorch 不要跟踪梯度變化。
* Ref
	* https://tree.rocks/deep-learning-from-scratch-pytorch-with-regression-5a12546299ea