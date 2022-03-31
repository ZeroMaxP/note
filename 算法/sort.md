## quick sort 快速排序

算法思想

1. 确定基准点x
2. 调整区间，使得第一个区间的值都小于x，第二个区间都大于x
3. 递归处理左右两端

```c++
#include <iostream>

using namespace std;

const int N = 1000010;

int q[N];

void quick_sort(int q[], int l, int r)
{
    if (l >= r) return;

    int i = l - 1, j = r + 1, x = q[l + r >> 1];
    while (i < j)
    {
        do i ++ ; while (q[i] < x);
        do j -- ; while (q[j] > x);
        if (i < j) swap(q[i], q[j]);
    }

    quick_sort(q, l, j);
    quick_sort(q, j + 1, r);
}

int main()
{
    int n;
    scanf("%d", &n);

    for (int i = 0; i < n; i ++ ) scanf("%d", &q[i]);

    quick_sort(q, 0, n - 1);

    for (int i = 0; i < n; i ++ ) printf("%d ", q[i]);

    return 0;
}

```

```c++
void quickSort(int q[], int l, int r) {
  if (l >= r) return;
  int pvoit = q[l], i = l, j = r;
  while(i < j) {
    // 如果取q[l]从右边开始，q[r]则从左边开始
    while(i < j && q[j] >= pvoit) j--;
    q[i] = q[j];
    while(i < j && q[i] <= pvoit) i++;
    q[j] = q[i];
  }
  q[i] = pvoit;
  quickSort(q, l, i - 1);
  quickSort(q, i + 1, r);
}

int main() {
  scanf("%d", &n);
  for(int i = 0; i < n; i++) scanf("%d", &q[i]);
  quickSort(q, 0, n - 1);
  for(int i = 0; i < n; i++) printf("%d ", q[i]);
  return 0;
}
```

### mergeSort 归并排序

算法思想:

1. 确定分界点mid = l + r >> 1
2. 递归排序s(l, mid), s(mid + 1, r)
3. 归并



