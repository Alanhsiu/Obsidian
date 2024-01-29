Hi, I'm Alan. I study Electrical Engineering at National Taiwan University. I've worked on many projects, covering both software and hardware, and I'm quite interested in programming. I really like facing new challenges and thinking creatively to solve problems, which keeps me constantly learning and improving.

- **Before starting coding, I want to check if my idea makes sense.**
- **The time/space complexity of this algorithm is O(log n) (Big O of log n)**

優點 I think I am a person who like to think and takes every task seriously. And also, I believe I can manage my time well.
缺點 One of weaknesses is asking for help when I need it. I’d like to do better at that.
目標 My primary goal is to gain more work experience. I’d like to learn more about the different aspects of being a good engineer.  
出國 I would go abroad for my graduate studies after 1 year later.  
延畢 I deferred my graduation for one semester to prepare my application for studying abroad.
問題 I wonder that when do you expect to be making your decision?

- Ｉ think this interview really valuable. Do you have any career advice for someone my age?


AM 10:00-10:45 (Albert, Pixel team)
Q1: Find max in an array.
Q2: Given an array with size N, consist of numbers with range [0, N-1], find if duplicate.

PM 2:30-3:15 (Ethan Lin)
Q1: On a beach, find a maximum continuous FREE vendors. (1D)
Q2: Find the maximum rectangle of $m*n$ array (all are true).

```cpp
#include <vector>
using namespace std;

int maximalRectangle(vector<vector<bool>>& matrix) {
    if (matrix.empty() || matrix[0].empty()) return 0;
    int m = matrix.size(), n = matrix[0].size();
    vector<vector<int>> width(m, vector<int>(n, 0));
    int maxArea = 0;

    for (int i = 0; i < m; ++i) {
        for (int j = 0; j < n; ++j) {
            if (!matrix[i][j]) continue;
            width[i][j] = (j == 0) ? 1 : width[i][j-1] + 1;
            int minWidth = width[i][j];

            for (int k = i; k >= 0; --k) {
                minWidth = min(minWidth, width[k][j]);
                if (minWidth == 0) break; 
                maxArea = max(maxArea, minWidth * (i - k + 1));
            }
        }
    }

    return maxArea;
}
```
