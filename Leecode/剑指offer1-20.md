## 1.数组中重复的数字

找出数组中重复的数字。


在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

示例 1：

输入：
[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3 


限制：

2 <= n <= 100000

### my solution

```c
//时间复杂度O(nlogn)，空间复杂度O(logn)
int cmp(const void *a, const void *b)
{
    return *(int*)a - *(int*)b;
}
int findRepeatNumber(int* nums, int numsSize){
    qsort(nums, numsSize, sizeof(int), cmp);
    int i = 0;
    while (i < numsSize - 1) {
        if (nums[i] == nums[i + 1]) return nums[i];
        i++;
    }
    return -1;
}
```

### 方法一：遍历数组

```java
//时间复杂度O(n)，空间复杂度O(n)
class Solution {
    public int findRepeatNumber(int[] nums) {
        Set<Integer> set = new HashSet<Integer>();
        int repeat = -1;
        for (int num : nums) {
            if (!set.add(num)) {
                repeat = num;
                break;
            }
        }
        return repeat;
    }
}
```

### 方法二：原地交换

```c++
//时间复杂度O(n)，空间复杂度O(1)
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        int i = 0;
        while(i < nums.size()) {
            if(nums[i] == i) {
                i++;
                continue;
            }
            if(nums[nums[i]] == nums[i])
                return nums[i];
            swap(nums[i],nums[nums[i]]);
        }
        return -1;
    }
};
```

### 方法三：标记法

```c++
//时间复杂度O(n)，空间复杂度O(1)
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        int n = nums.size();
        for(int i = 0; i < n; i++){
            int k = nums[i];
            if(k < 0) k += n;
            if(nums[k] < 0) return k;
            nums[k] -= n;
        }
        return -1;
    }
};
```

## 2.二维数组中的查找

在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

示例:

现有矩阵 matrix 如下：

[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
给定 target = 5，返回 true。

给定 target = 20，返回 false。

限制：

0 <= n <= 1000

0 <= m <= 1000

### my solution

```c
// 时间复杂度O(nm)，空间复杂度O(1)
bool findNumberIn2DArray(int** matrix, int matrixSize, int* matrixColSize, int target){
    if (matrixSize == 0 || *matrixColSize == 0 || matrix[0][0] > target || matrix[matrixSize - 1][*matrixColSize - 1] < target) return false;
    int rowLeft = 0, rowRight = matrixSize - 1, n = 0;
    bool leftGet = false, rightGet = false;
    while(n < matrixSize && !(leftGet && rightGet)) {
        if (matrix[n][0] == target || matrix[n][*matrixColSize - 1] == target) return true;
        if (!rightGet && matrix[n][0] > target) {
            rowRight = n - 1;
            rightGet = true;
        }
        if (!leftGet && matrix[n][*matrixColSize - 1] > target) {
            rowLeft = n;
            leftGet = true;
        }
        n++;
    }
    for(int i = rowLeft; i <= rowRight; i++) {
        for(int j = 0; j < *matrixColSize; j++) {
        if (matrix[i][j] == target) return true;
        if (matrix[i][j] > target) break;
        }
    }
    return false;
}
```

### 方法一：暴力

```java
// 时间复杂度O(nm)，空间复杂度O(1)
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return false;
        }
        int rows = matrix.length, columns = matrix[0].length;
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < columns; j++) {
                if (matrix[i][j] == target) {
                    return true;
                }
            }
        }
        return false;
    }
}
```

### 方法二：线性查找

```java
// 时间复杂度O(n+m)，空间复杂度O(1)
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return false;
        }
        int rows = matrix.length, columns = matrix[0].length;
        int row = 0, column = columns - 1;
        while (row < rows && column >= 0) {
            int num = matrix[row][column];
            if (num == target) {
                return true;
            } else if (num > target) {
                column--;
            } else {
                row++;
            }
        }
        return false;
    }
}
```

## 3.替换空格

请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

示例 1：

输入：s = "We are happy."
输出："We%20are%20happy."


限制：

0 <= s 的长度 <= 10000

### my solution

```c
// 时间复杂度O(len)，空间复杂度O(len)
char* replaceSpace(char* s){
    int len = strlen(s);
    char* res = (char*) malloc(sizeof(char) * len * 3 + 1);
    int i = 0, j = 0;
    while(s[i] != '\0') {
        if (s[i] != ' ') {
            res[j++] = s[i++];
        } else {
            i++;
            res[j++] = '%',
            res[j++] = '2';
            res[j++] = '0';
        }
    }
    res[j++] = '\0';
    return res;
}
```

### 方法一：字符数组

```java
// 时间复杂度O(len)，空间复杂度O(len)
class Solution {
    public String replaceSpace(String s) {
        int length = s.length();
        char[] array = new char[length * 3];
        int size = 0;
        for (int i = 0; i < length; i++) {
            char c = s.charAt(i);
            if (c == ' ') {
                array[size++] = '%';
                array[size++] = '2';
                array[size++] = '0';
            } else {
                array[size++] = c;
            }
        }
        String newStr = new String(array, 0, size);
        return newStr;
    }
}
```

```c++
class Solution {
public:
    string replaceSpace(string s) {
        int count = 0, length = s.length();

        for (int i = 0; i < length; i++) {
            if (s[i] == ' ') {
                count++;
            }
        }

        if (count == 0) {
            return s;
        }

        for (int i = 0; i < count; i++) {
            s += "00";
        }

        int new_length = s.length();

        int j = new_length - 1;

        for (int i = length - 1; i >= 0; i--) {
            if (s[i] != ' ') {
                s[j--] = s[i];
            } else {
                s[j--] = '0';
                s[j--] = '2';
                s[j--] = '%';
            }
        }

        return s;
    }
};
```

## 4.从尾到头打印链表

输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

示例 1：

输入：head = [1,3,2]
输出：[2,3,1]


限制：

0 <= 链表长度 <= 10000

### my solution

```c
//时间复杂度O(n)，空间复杂度O(n)
int* reversePrint(struct ListNode* head, int* returnSize){
    struct ListNode *stk = NULL;
    *returnSize = 0;
    while (head) {
        struct ListNode* node = malloc(sizeof(struct ListNode));
        node->next = stk;
        node->val = head->val;
        head = head->next;
        stk = node;
        *returnSize += 1;
    }
    int* res = (int*)malloc(sizeof(int)**returnSize);
    int i = 0;
    while(stk) {
        res[i++] = stk->val;
        stk = stk->next;
    }
    return res;
}
```

### 方法一：栈

```java
//时间复杂度O(n)，空间复杂度O(n)
class Solution {
    public int[] reversePrint(ListNode head) {
        Stack<ListNode> stack = new Stack<ListNode>();
        ListNode temp = head;
        while (temp != null) {
            stack.push(temp);
            temp = temp.next;
        }
        int size = stack.size();
        int[] print = new int[size];
        for (int i = 0; i < size; i++) {
            print[i] = stack.pop().val;
        }
        return print;
    }
}
```

### 方法二：递归法

```java
class Solution {
    int[] res;
    int i = 0;
    int j = 0;
    public int[] reversePrint(ListNode head) {
        solve(head);
        return res;
    }
    public void solve(ListNode head){
        if(head == null){
            res = new int[i];
            return;
        }
        i++; 
        solve(head.next);
        res[j] = head.val;
        j++;
    }
}
```

## 🔴5.重建二叉树

输入某二叉树的前序遍历和中序遍历的结果，请重建该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

例如，给出

前序遍历 preorder = [3,9,20,15,7]
中序遍历 inorder = [9,3,15,20,7]
返回如下的二叉树：

        3
       / \
      9  20
        /  \
       15   7

限制：

0 <= 节点个数 <= 5000

### my solution

```c
// 时间复杂度O(n)，空间复杂度O(n)
struct stackNode {
    struct TreeNode* val;
    struct stackNode* next;
};

struct stackNode* stk = NULL;

struct TreeNode* makeTreeNode(int v) {
    struct TreeNode* node = malloc(sizeof(struct TreeNode));
    node->val = v;
    node->left = NULL;
    node->right = NULL;
    return node;
}

void push(struct TreeNode* v) {
    struct stackNode* node= malloc(sizeof(struct stackNode));
    node->val = v;
    node->next = stk;
    stk = node;
}

void pop() {
    stk = stk->next;
}

struct stackNode* getTop() {
    return stk;
}

struct TreeNode* buildTree(int* preorder, int preorderSize, int* inorder, int inorderSize){
    if (!preorderSize) return NULL;
    stk = NULL;
    struct TreeNode* root = makeTreeNode(preorder[0]);
    push(root);
    int inorderIndex = 0;
    for(int i = 1; i < preorderSize; i++) {
        int preorderVal = preorder[i];
        struct stackNode* top = getTop();
        struct TreeNode* node = top->val;
        if(node->val != inorder[inorderIndex]) {
            node->left = makeTreeNode(preorderVal);
            push(node->left);
        } else {
            while(stk && getTop()->val->val == inorder[inorderIndex]) {
                top = getTop();
                node = top->val;
                pop();
                inorderIndex++;
            }
            node->right = makeTreeNode(preorderVal);
            push(node->right);
        }
    }
    return root;
}
```

二叉树前序遍历的顺序为：

先遍历根节点；

随后递归地遍历左子树；

最后递归地遍历右子树。

二叉树中序遍历的顺序为：

先递归地遍历左子树；

随后遍历根节点；

最后递归地遍历右子树。

在「递归」地遍历某个子树的过程中，我们也是将这颗子树看成一颗全新的树，按照上述的顺序进行遍历。挖掘「前序遍历」和「中序遍历」的性质，我们就可以得出本题的做法。

### 方法一：递归

思路

对于任意一颗树而言，前序遍历的形式总是


[ 根节点, [左子树的前序遍历结果], [右子树的前序遍历结果] ]
即根节点总是前序遍历中的第一个节点。而中序遍历的形式总是


[ [左子树的中序遍历结果], 根节点, [右子树的中序遍历结果] ]
只要我们在中序遍历中定位到根节点，那么我们就可以分别知道左子树和右子树中的节点数目。由于同一颗子树的前序遍历和中序遍历的长度显然是相同的，因此我们就可以对应到前序遍历的结果中，对上述形式中的所有左右括号进行定位。

这样以来，我们就知道了左子树的前序遍历和中序遍历结果，以及右子树的前序遍历和中序遍历结果，我们就可以递归地对构造出左子树和右子树，再将这两颗子树接到根节点的左右位置。

细节

在中序遍历中对根节点进行定位时，一种简单的方法是直接扫描整个中序遍历的结果并找出根节点，但这样做的时间复杂度较高。我们可以考虑使用哈希表来帮助我们快速地定位根节点。对于哈希映射中的每个键值对，键表示一个元素（节点的值），值表示其在中序遍历中的出现位置。在构造二叉树的过程之前，我们可以对中序遍历的列表进行一遍扫描，就可以构造出这个哈希映射。在此后构造二叉树的过程中，我们就只需要 O(1)O(1) 的时间对根节点进行定位了。

下面的代码给出了详细的注释。

```c++
// 时间复杂度O(n)，空间复杂度O(n)
class Solution {
private:
    unordered_map<int, int> index;

public:
    TreeNode* myBuildTree(const vector<int>& preorder, const vector<int>& inorder, int preorder_left, int preorder_right, int inorder_left, int inorder_right) {
        if (preorder_left > preorder_right) {
            return nullptr;
        }
        
        // 前序遍历中的第一个节点就是根节点
        int preorder_root = preorder_left;
        // 在中序遍历中定位根节点
        int inorder_root = index[preorder[preorder_root]];
        
        // 先把根节点建立出来
        TreeNode* root = new TreeNode(preorder[preorder_root]);
        // 得到左子树中的节点数目
        int size_left_subtree = inorder_root - inorder_left;
        // 递归地构造左子树，并连接到根节点
        // 先序遍历中「从 左边界+1 开始的 size_left_subtree」个元素就对应了中序遍历中「从 左边界 开始到 根节点定位-1」的元素
        root->left = myBuildTree(preorder, inorder, preorder_left + 1, preorder_left + size_left_subtree, inorder_left, inorder_root - 1);
        // 递归地构造右子树，并连接到根节点
        // 先序遍历中「从 左边界+1+左子树节点数目 开始到 右边界」的元素就对应了中序遍历中「从 根节点定位+1 到 右边界」的元素
        root->right = myBuildTree(preorder, inorder, preorder_left + size_left_subtree + 1, preorder_right, inorder_root + 1, inorder_right);
        return root;
    }

    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        int n = preorder.size();
        // 构造哈希映射，帮助我们快速定位根节点
        for (int i = 0; i < n; ++i) {
            index[inorder[i]] = i;
        }
        return myBuildTree(preorder, inorder, 0, n - 1, 0, n - 1);
    }
};
```

### 方法二：迭代
思路

迭代法是一种非常巧妙的实现方法。

对于前序遍历中的任意两个连续节点 u 和 v，根据前序遍历的流程，我们可以知道 u 和 v 只有两种可能的关系：

v 是 u 的左儿子。这是因为在遍历到 u 之后，下一个遍历的节点就是 u 的左儿子，即 v；

u 没有左儿子，并且 v 是 u 的某个祖先节点（或者 u 本身）的右儿子。如果 u 没有左儿子，那么下一个遍历的节点就是 u 的右儿子。如果 u 没有右儿子，我们就会向上回溯，直到遇到第一个有右儿子（且 u 不在它的右儿子的子树中）的节点 ua，那么 v 就是 ua的右儿子。

第二种关系看上去有些复杂。我们举一个例子来说明其正确性，并在例子中给出我们的迭代算法。

例子

我们以树


            3
           / \
          9  20
         /  /  \
        8  15   7
       / \
      5  10
     /
    4

为例，它的前序遍历和中序遍历分别为


preorder = [3, 9, 8, 5, 4, 10, 20, 15, 7]
inorder = [4, 5, 8, 10, 9, 3, 15, 20, 7]
我们用一个栈 stack 来维护「当前节点的所有还没有考虑过右儿子的祖先节点」，栈顶就是当前节点。也就是说，只有在栈中的节点才可能连接一个新的右儿子。同时，我们用一个指针 index 指向中序遍历的某个位置，初始值为 0。index 对应的节点是「当前节点不断往左走达到的最终节点」，这也是符合中序遍历的，它的作用在下面的过程中会有所体现。

首先我们将根节点 3 入栈，再初始化 index 所指向的节点为 4，随后对于前序遍历中的每个节点，我们依次判断它是栈顶节点的左儿子，还是栈中某个节点的右儿子。

我们遍历 9。9 一定是栈顶节点 3 的左儿子。我们使用反证法，假设 9 是 3 的右儿子，那么 3 没有左儿子，index 应该恰好指向 3，但实际上为 4，因此产生了矛盾。所以我们将 9 作为 3 的左儿子，并将 9 入栈。

stack = [3, 9]
index -> inorder[0] = 4
我们遍历 8，5 和 4。同理可得它们都是上一个节点（栈顶节点）的左儿子，所以它们会依次入栈。

stack = [3, 9, 8, 5, 4]
index -> inorder[0] = 4
我们遍历 10，这时情况就不一样了。我们发现 index 恰好指向当前的栈顶节点 4，也就是说 4 没有左儿子，那么 10 必须为栈中某个节点的右儿子。那么如何找到这个节点呢？栈中的节点的顺序和它们在前序遍历中出现的顺序是一致的，而且每一个节点的右儿子都还没有被遍历过，那么这些节点的顺序和它们在中序遍历中出现的顺序一定是相反的。

这是因为栈中的任意两个相邻的节点，前者都是后者的某个祖先。并且我们知道，栈中的任意一个节点的右儿子还没有被遍历过，说明后者一定是前者左儿子的子树中的节点，那么后者就先于前者出现在中序遍历中。

因此我们可以把 index 不断向右移动，并与栈顶节点进行比较。如果 index 对应的元素恰好等于栈顶节点，那么说明我们在中序遍历中找到了栈顶节点，所以将 index 增加 1 并弹出栈顶节点，直到 index 对应的元素不等于栈顶节点。按照这样的过程，我们弹出的最后一个节点 x 就是 10 的双亲节点，这是因为 10 出现在了 x 与 x 在栈中的下一个节点的中序遍历之间，因此 10 就是 x 的右儿子。

回到我们的例子，我们会依次从栈顶弹出 4，5 和 8，并且将 index 向右移动了三次。我们将 10 作为最后弹出的节点 8 的右儿子，并将 10 入栈。

stack = [3, 9, 10]
index -> inorder[3] = 10
我们遍历 20。同理，index 恰好指向当前栈顶节点 10，那么我们会依次从栈顶弹出 10，9 和 3，并且将 index 向右移动了三次。我们将 20 作为最后弹出的节点 3 的右儿子，并将 20 入栈。

stack = [20]
index -> inorder[6] = 15
我们遍历 15，将 15 作为栈顶节点 20 的左儿子，并将 15 入栈。

stack = [20, 15]
index -> inorder[6] = 15
我们遍历 7。index 恰好指向当前栈顶节点 15，那么我们会依次从栈顶弹出 15 和 20，并且将 index 向右移动了两次。我们将 7 作为最后弹出的节点 20 的右儿子，并将 7 入栈。

stack = [7]
index -> inorder[8] = 7
此时遍历结束，我们就构造出了正确的二叉树。

算法

我们归纳出上述例子中的算法流程：

我们用一个栈和一个指针辅助进行二叉树的构造。初始时栈中存放了根节点（前序遍历的第一个节点），指针指向中序遍历的第一个节点；

我们依次枚举前序遍历中除了第一个节点以外的每个节点。如果 index 恰好指向栈顶节点，那么我们不断地弹出栈顶节点并向右移动 index，并将当前节点作为最后一个弹出的节点的右儿子；如果 index 和栈顶节点不同，我们将当前节点作为栈顶节点的左儿子；

无论是哪一种情况，我们最后都将当前的节点入栈。

最后得到的二叉树即为答案。

## 🔴6.用两个栈实现队列

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )

示例 1：

输入：
["CQueue","appendTail","deleteHead","deleteHead"]
[[],[3],[],[]]
输出：[null,null,3,-1]
示例 2：

输入：
["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]
[[],[],[5],[2],[],[]]
输出：[null,-1,null,null,5,2]
提示：

1 <= values <= 10000
最多会对 appendTail、deleteHead 进行 10000 次调用

### my solution

```c
struct stackNode {
    int val;
    struct stackNode* next;    
};

typedef struct {
    struct stackNode* val;
    struct stackNode* temp;
} CQueue;

CQueue* cQueueCreate() {
    CQueue *queue = (CQueue*)malloc(sizeof(CQueue));
    if(queue==NULL)
    {
        return NULL;
    }
    queue->val = NULL;
    queue->temp = NULL;
    return queue;
}

void cQueueAppendTail(CQueue* obj, int value) {
    struct stackNode* node = malloc(sizeof(struct stackNode));
    node->val = value;
    node->next = obj->val;
    obj->val = node;
}

int cQueueDeleteHead(CQueue* obj) {
    if(!obj->temp) {
        if (!obj->val) return -1;
        while(obj->val) {
            struct stackNode* node = malloc(sizeof(struct stackNode));
            node->val = obj->val->val;
            node->next = obj->temp;
            obj->temp = node;
            obj->val = obj->val->next;
        }
    }
    int value = obj->temp->val;
    obj->temp = obj->temp->next;
    return value;
}

void cQueueFree(CQueue* obj) {
    free(obj);
}

/**
 * Your CQueue struct will be instantiated and called as such:
 * CQueue* obj = cQueueCreate();
 * cQueueAppendTail(obj, value);
 
 * int param_2 = cQueueDeleteHead(obj);
 
 * cQueueFree(obj);
*/
```

### 方法一：双栈

```c++
//时间复杂度O(1)，空间复杂度O(n)
class CQueue {
    stack<int> stack1,stack2;
public:
    CQueue() {
        while (!stack1.empty()) {
            stack1.pop();
        }
        while (!stack2.empty()) {
            stack2.pop();
        }
    }
    
    void appendTail(int value) {
        stack1.push(value);
    }
    
    int deleteHead() {
        // 如果第二个栈为空
        if (stack2.empty()) {
            while (!stack1.empty()) {
                stack2.push(stack1.top());
                stack1.pop();
            }
        } 
        if (stack2.empty()) {
            return -1;
        } else {
            int deleteItem = stack2.top();
            stack2.pop();
            return deleteItem;
        }
    }
};
```

## 7.斐波那契数列

写一个函数，输入 n ，求斐波那契（Fibonacci）数列的第 n 项（即 F(N)）。斐波那契数列的定义如下：

F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), 其中 N > 1.
斐波那契数列由 0 和 1 开始，之后的斐波那契数就是由之前的两数相加而得出。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

示例 1：

输入：n = 2
输出：1
示例 2：

输入：n = 5
输出：5


提示：

0 <= n <= 100

### my solution

```c
//时间复杂度o(n)，空间复杂度O(1)
int fib(int n){
    switch(n) {
        case 0:
            return 0;
            break;
        case 1:
            return 1;
            break;
        default:
        {
            int f1 = 0, f2 = 1;
            int res = 2;
            n-=2;
            while (n-- >= 0) {
                res = f2 + f1;
                if (res > 1000000007) res -= 1000000007;
                f1 = f2;
                f2 = res;
            }
            return res;
        }
    }
}
```

### **递归法：**

### **记忆化递归法：**

### **动态规划：**

```java
class Solution {
    public int fib(int n) {
        int a = 0, b = 1, sum;
        for(int i = 0; i < n; i++){
            sum = (a + b) % 1000000007;
            a = b;
            b = sum;
        }
        return a;
    }
}
```

## 8. 青蛙跳台阶问题

一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

示例 1：

输入：n = 2
输出：2
示例 2：

输入：n = 7
输出：21
示例 3：

输入：n = 0
输出：1
提示：

0 <= n <= 100

### my solution

```c
//时间复杂度O(n)，空间复杂度O(1)
int numWays(int n){
    switch(n) {
        case 0: 
          return 1;
        case 1: 
          return 1;
        case 2:
          return 2;
        default: {
          int p = 1, q = 2, r = 3;
          n-=2; 
          while(n-- > 0) {
            r = p + q;
            if (r > 1000000007) r -= 1000000007;
            p = q;
            q = r;
          }
          return r;
        }
    }
}
```

```java
class Solution {
    public int numWays(int n) {
        int a = 1, b = 1, sum;
        for(int i = 0; i < n; i++){
            sum = (a + b) % 1000000007;
            a = b;
            b = sum;
        }
        return a;
    }
}
```

## 9.旋转数组的最小数字

把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。  

示例 1：

输入：[3,4,5,1,2]
输出：1
示例 2：

输入：[2,2,2,0,1]
输出：0

### my solution

```c
//时间复杂度O(n)，空间复杂度O(1)
int minArray(int* numbers, int numbersSize){
  for (int i = 0; i < numbersSize - 1; i++)
    if (numbers[i] > numbers[i + 1]) return numbers[i + 1];
  return numbers[0];
}
```

### 二分查找

```c
//时间复杂度O(n)，空间复杂度O(1)
int minArray(int* numbers, int numbersSize) {
    int low = 0;
    int high = numbersSize - 1;
    while (low < high) {
        int pivot = low + (high - low) / 2;
        if (numbers[pivot] < numbers[high]) {
            high = pivot;
        } else if (numbers[pivot] > numbers[high]) {
            low = pivot + 1;
        } else {
            high -= 1;
        }
    }
    return numbers[low];
}
```

## 🔴10.矩阵中的路径


给定一个 m x n 二维字符网格 board 和一个字符串单词 word 。如果 word 存在于网格中，返回 true ；否则，返回 false 。

单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。

例如，在下面的 3×4 的矩阵中包含单词 "ABCCED"（单词中的字母已标出）。

![img](%E5%89%91%E6%8C%87offer1-20.assets/word2.jpg)

示例 1：

输入：board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
输出：true
示例 2：

输入：board = [["a","b"],["c","d"]], word = "abcd"
输出：false


提示：

1 <= board.length <= 200
1 <= board[i].length <= 200
board 和 word 仅由大小写英文字母组成

### my solution

DFS 解析：
递归参数： 当前元素在矩阵 board 中的行列索引 i 和 j ，当前目标字符在 word 中的索引 k 。
终止条件：
返回 false ： (1) 行或列索引越界 或 (2) 当前矩阵元素与目标字符不同 或 (3) 当前矩阵元素已访问过 （ (3) 可合并至 (2) ） 。
返回 true ： k = len(word) - 1 ，即字符串 word 已全部匹配。
递推工作：
标记当前矩阵元素： 将 board[i][j]修改为 空字符 '' ，代表此元素已访问过，防止之后搜索时重复访问。
搜索下一单元格： 朝当前元素的 上、下、左、右 四个方向开启下层递归，使用 或 连接 （代表只需找到一条可行路径就直接返回，不再做后续 DFS ），并记录结果至 res 。
还原当前矩阵元素： 将 board[i][j] 元素还原至初始值，即 word[k] 。
返回值： 返回布尔量 res ，代表是否搜索到目标字符串。

```c++
//时间复杂度O(MN)，空间复杂度O(MN)
class Solution {
public:
    bool pathSearch(vector<vector<char>>& board, int row, int col, string word, int index) {
        if (row < 0 || col < 0 || row >= board.size() || col >= board[0].size() || board[row][col] != word[index] ) return false;
        if (index == word.length() - 1) return true;
        board[row][col] = '\0';
        bool res =  pathSearch(board, row - 1, col, word, index + 1) || pathSearch(board, row + 1, col, word, index + 1) || pathSearch(board, row, col - 1, word, index + 1) || pathSearch(board, row, col + 1, word, index + 1);
        board[row][col] = word[index];
        return res;
    }
    bool exist(vector<vector<char>>& board, string word) {
        for(int i = 0; i < board.size(); i++) {
            for(int j = 0; j < board[i].size(); j++) {
                if (board[i][j] == word[0])
                    if (pathSearch(board, i, j, word, 0)) return true;
            }
        }
        return false;
    }
};
```

```java
class Solution {
    public boolean exist(char[][] board, String word) {
        char[] words = word.toCharArray();
        for(int i = 0; i < board.length; i++) {
            for(int j = 0; j < board[0].length; j++) {
                if(dfs(board, words, i, j, 0)) return true;
            }
        }
        return false;
    }
    boolean dfs(char[][] board, char[] word, int i, int j, int k) {
        if(i >= board.length || i < 0 || j >= board[0].length || j < 0 || board[i][j] != word[k]) return false;
        if(k == word.length - 1) return true;
        board[i][j] = '\0';
        boolean res = dfs(board, word, i + 1, j, k + 1) || dfs(board, word, i - 1, j, k + 1) || 
                      dfs(board, word, i, j + 1, k + 1) || dfs(board, word, i , j - 1, k + 1);
        board[i][j] = word[k];
        return res;
    }
}
```

## 🔴11.机器人的运动范围

地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

示例 1：

输入：m = 2, n = 3, k = 1
输出：3
示例 2：

输入：m = 3, n = 1, k = 0
输出：1
提示：

1 <= n,m <= 100
0 <= k <= 20

### 方法一：深度优先遍历 DFS

数位和增量公式： 设 x 的数位和为 s_x ， x+1 的数位和为 s_x+1 ；
当 (x + 1) %10 = 0时： s{x+1} = s_x - 8，例如 19, 20的数位和分别为 10, 2;
当 (x + 1) %10 != 0 时： s{x+1} = s_x + 1，例如 1, 2 的数位和分别为 1, 2。

```c++
(x + 1) % 10 != 0 ? s_x + 1 : s_x - 8;
```

```c++
//时间复杂度O(mn)，空间复杂度O(mn)
class Solution {
public:
    int movingCount(int m, int n, int k) {
        vector<vector<bool>> visited(m, vector<bool>(n, 0));
        return dfs(0, 0, 0, 0, visited, m, n, k);
    }
private:
    int dfs(int i, int j, int si, int sj, vector<vector<bool>> &visited, int m, int n, int k) {
        if(i >= m || j >= n || k < si + sj || visited[i][j]) return 0;
        visited[i][j] = true;
        return 1 + dfs(i + 1, j, (i + 1) % 10 != 0 ? si + 1 : si - 8, sj, visited, m, n, k) +
                   dfs(i, j + 1, si, (j + 1) % 10 != 0 ? sj + 1 : sj - 8, visited, m, n, k);
    }
};
```

### 方法二：广度优先遍历 BFS

```c++
//时间复杂度O(mn)，空间复杂度O(mn)
class Solution {
public:
    int movingCount(int m, int n, int k) {
        vector<vector<bool>> visited(m, vector<bool>(n, 0));
        int res = 0;
        queue<vector<int>> que;
        que.push({ 0, 0, 0, 0 });
        while(que.size() > 0) {
            vector<int> x = que.front();
            que.pop();
            int i = x[0], j = x[1], si = x[2], sj = x[3];
            if(i >= m || j >= n || k < si + sj || visited[i][j]) continue;
            visited[i][j] = true;
            res++;
            que.push({ i + 1, j, (i + 1) % 10 != 0 ? si + 1 : si - 8, sj });
            que.push({ i, j + 1, si, (j + 1) % 10 != 0 ? sj + 1 : sj - 8 });
        }
        return res;
    }
};
```

### 方法三：递推

定义 ```vis[i][j]``` 为 (i, j) 坐标是否可达，如果可达返回 1，否则返回 0。

首先 (i, j) 本身需要可以进入，因此需要先判断 i 和 j 的数位之和是否大于 k ，如果大于的话直接设置```vis[i][j]```为不可达即可。

否则，前面提到搜索方向只需朝下或朝右，因此 (i, j) 的格子只会从 (i - 1, j) 或者 (i, j - 1) 两个格子走过来（不考虑边界条件），那么 ```vis[i][j]```是否可达的状态则可由如下公式计算得到：

```c++
/*vis[i][j]=vis[i−1][j] or vis[i][j−1]
即只要有一个格子可达，那么 (i, j) 这个格子就是可达的，因此我们只要遍历所有格子，递推计算出它们是否可达然后用变量 ans 记录可达的格子数量即可。
初始条件 vis[i][j] = 1 ，递推计算的过程中注意边界的处理。*/
class Solution {
    int get(int x) {
        int res=0;
        for (; x; x /= 10){
            res += x % 10;
        }
        return res;
    }
public:
    int movingCount(int m, int n, int k) {
        if (!k) return 1;
        vector<vector<int> > vis(m, vector<int>(n, 0));
        int ans = 1;
        vis[0][0] = 1;
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                if ((i == 0 && j == 0) || get(i) + get(j) > k) continue;
                // 边界判断
                if (i - 1 >= 0) vis[i][j] |= vis[i - 1][j];
                if (j - 1 >= 0) vis[i][j] |= vis[i][j - 1];
                ans += vis[i][j];
            }
        }
        return ans;
    }
};

## 🔴12.剪绳子

给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 k[0],k[1]...k[m-1] 。请问 k[0]k[1]...k[m-1] 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。

示例 1：

输入: 2
输出: 1
解释: 2 = 1 + 1, 1 × 1 = 1
示例 2:

输入: 10
输出: 36
解释: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36
提示：

2 <= n <= 58

### 方法一：数学推导

题解https://leetcode-cn.com/problems/jian-sheng-zi-lcof/solution/mian-shi-ti-14-i-jian-sheng-zi-tan-xin-si-xiang-by/

​```java
class Solution {
    public int cuttingRope(int n) {
        if(n <= 3) return n - 1;
        int a = n / 3, b = n % 3;
        if(b == 0) return (int)Math.pow(3, a);
        if(b == 1) return (int)Math.pow(3, a - 1) * 4;
        return (int)Math.pow(3, a) * 2;
    }
}
```

### 方法二：贪心思想

### 方法三：动态规划

```c++
class Solution {
public:
    int cuttingRope(int n) {
        if (n < 4) return n - 1;
        vector<int> products(n + 1, 0);
        products[1] = 1;
        products[2] = 2;
        products[3] = 3;
        int max_val = 0;
        for (int i = 4; i <= n; i ++){
            max_val = 0;
            for (int j = 1; j <= i/2; j ++){
                max_val = max(max_val, products[j] * products[i-j]);
            }
        products[i] = max_val;
        }
        return products[n];
    }
};
```

##  17. 打印从1到最大的n位数

https://leetcode-cn.com/problems/da-yin-cong-1dao-zui-da-de-nwei-shu-lcof/

```c++
class Solution {
public:
    int size, start;
    int count = 0, nine = 0;
    string loop = "0123456789";
    void dfs(vector<int> &ans, string &s, int n) {
        while(n == size) {
            string str = s.substr(start);
            if (str[0] != '0') ans.push_back(std::stoi(str));
            if (n - start == nine) start--;
            return ;
        }
        for(char i: loop) {
            printf("%c", i);
            s[n] = i;
            if (i == '9') nine++;
            dfs(ans, s, n + 1);
        }
        nine --;
    }
    vector<int> printNumbers(int n) {
        start = n - 1;
        size = n;
        string path(n, '0');
        vector<int> ans;
        dfs(ans, path, 0);
        return ans;
    }
};
```



## my solution

```c++
class Solution {
public:
    int hammingWeight(uint32_t n) {
        int cnt = 0;
        while(n) {
            if (n % 2 == 1) cnt++;
            n = n / 2;
        }
        return cnt;
    }
};
```

### 方法一：逐位判断

```java
public class Solution {
    public int hammingWeight(int n) {
        int res = 0;
        while(n != 0) {
            res += n & 1;
            n >>>= 1;
        }
        return res;
    }
}
```

### 方法二：巧用 n \& (n - 1)

![Picture10.png](%E5%89%91%E6%8C%87offer1-20.assets/9bc8ab7ba242888d5291770d35ef749ae76ee2f1a51d31d729324755fc4b1b1c-Picture10.png)

初始化数量统计变量 res 。
循环消去最右边的 11 ：当 n = 0时跳出。
res += 1 ： 统计变量加 11 ；
n &= n - 1 ： 消去数字 n最右边的 1 。

```java
//时间复杂度O(M)，空间复杂度O(1)
public class Solution {
    public int hammingWeight(int n) {
        int res = 0;
        while(n != 0) {
            res++;
            n &= n - 1;
        }
        return res;
    }
}
```

## 12