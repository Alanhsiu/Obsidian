* [note link](https://chsiang.notion.site/647db86ee9c04d899f1bd7643e4d94cd?v=87bcbe3e176e422aa85cfb86900c5fd6)
* 機器學習的不同類型
	1. **Regression:** The function outputs a scalar.
	2. **Classification**: Given options (classes), the function outputs the correct one.
	3. **Structured learning**: The function learns to map input data to structured output data, which can be more complex than a simple scalar or class label.
* 訓練三步驟
	1. Function with Unknown Parameters
		* Feature ($x_1$)
		* Weight ($w$)
		* Bias ($b$)
	2. Define Loss from Training Data
		* MAE (mean absolute error)
		* MSE (mean square error)
		* Cross-entropy: a measure of the difference between two probability distributions.
		* Error surface: graphical representation of the relationship between the model's parameters and its associated error or loss function.
	3. Optimization
		 * Gradient Descent