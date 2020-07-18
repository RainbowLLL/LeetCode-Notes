## DFS和BFS比较
BFS 
1.空间是指数级别 大可以搜出最小方案
2.不会有爆栈的风险
3.最短、最小

DFS 
1.空间和树的深度成正比 小
2.有爆栈风险，比如树的深度最坏可能有100000层，栈空间为4M
3.不能搜最短、最小

一般DFS好写一些

## leetcode 111 二叉树的最小深度 DFS
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int minDepth(TreeNode* root) {
        if(!root) return 0;
        int left = minDepth(root->left);
        int right = minDepth(root->right);
        if(!left || !right) return left + right + 1; // 如果有一个子树为空，返回另外一个子树深度
        return min(left, right) + 1;
    }
};

## leetcode 279 完全平方数 BFS
## leetcode 733 图像渲染 DFS

要判断当前颜色和新颜色是否相等
```
class Solution {
public:
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int newColor) {
        if(image.empty() || image[0].empty()) return image;
        int dx[4] = {-1,0,1,0};
        int dy[4] = {0,1,0,-1};
        int oldcolor = image[sr][sc];
        if(oldcolor == newColor) return image;
        image[sr][sc] = newColor;
        for(int i = 0; i < 4 ;i++)
        {
            int x = sr + dx[i], y = sc + dy[i];
            if(x >= 0 && x < image.size() && y >= 0 && y < image[0].size() && image[x][y] == oldcolor)
                floodFill(image,x,y,newColor);
        }
        return image;
    }
  ```
};
