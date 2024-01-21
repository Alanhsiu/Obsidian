### CUDA的核心概念：

1. **GPU架構**：GPU由許多小的、高效能的核心組成，這使得它們非常適合於進行高度平行的計算任務。
2. **核心（Kernel）**：在CUDA編程中，一個核心是一段在GPU上執行的代碼。這個核心可以被多個不同的執行緒同時執行。
3. **執行緒和執行緒塊（Thread & Block）**：CUDA把執行任務的執行緒組織成執行緒塊。每個執行緒塊可以包含多個執行緒，並且多個執行緒塊可以組成一個網格（Grid）。
4. **記憶體管理**：理解和有效管理GPU的記憶體是至關重要的。CUDA有不同類型的記憶體，包括全局記憶體、共享記憶體、常數記憶體和紋理記憶體。
5. **同步和錯誤處理**：學習如何同步執行緒和處理可能出現的錯誤也是重要的。

### 實際範例：

讓我們來看一個簡單的例子：向量加法。在這個例子中，我們有兩個大小相同的向量，我們要將這兩個向量的相應元素相加，並將結果儲存在另一個向量中。

首先，我們需要寫一個CUDA核心來執行這個任務：
```
__global__ void vectorAdd(int *a, int *b, int *c, int n) {
    int index = threadIdx.x + blockIdx.x * blockDim.x;
    if (index < n) {
        c[index] = a[index] + b[index];
    }
}
```
在這段代碼中，`__global__`標記表明`vectorAdd`是一個在GPU上運行的核心。每個執行緒會計算出它的唯一索引，並對相應的元素進行加法操作。

接下來，我們需要從主機代碼中調用這個核心：
```int main() {
    int n = 1000;  // 假設向量大小為1000
    int *a, *b, *c;
    int *d_a, *d_b, *d_c;  // GPU記憶體中的指標

    // 為向量分配主機和設備記憶體
    a = (int *)malloc(n * sizeof(int));
    b = (int *)malloc(n * sizeof(int));
    c = (int *)malloc(n * sizeof(int));
    cudaMalloc(&d_a, n * sizeof(int));
    cudaMalloc(&d_b, n * sizeof(int));
    cudaMalloc(&d_c, n * sizeof(int));

    // 初始化向量a和b...

    // 將數據從主機複製到設備
    cudaMemcpy(d_a, a, n * sizeof(int), cudaMemcpyHostToDevice);
    cudaMemcpy(d_b, b, n * sizeof(int), cudaMemcpyHostToDevice);

    // 執行核心
    vectorAdd<<<(n + 255)/256, 256>>>(d_a, d_b, d_c, n);

    // 將結果從設備複製回主機
    cudaMemcpy(c, d_c, n * sizeof(int), cudaMemcpyDeviceToHost);

    // 清理
    cudaFree(d_a); cudaFree(d_b); cudaFree(d_c);
    free(a); free(b); free(c);

    return 0;
}
```
在這段代碼中，我們首先在主機和設備上為數據分配記憶體，然後初始化數據並將其傳輸到GPU。接著，我們調用了之前寫的核心，並且在最後將結果從GPU傳回到主機。