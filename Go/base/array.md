### 声明

```go
var 数组变量名 [元素数量]T
```

### 初始化

```go
var team = [...]string{"hammer", "soldier", "mum"}
```

### 遍历

```go
var team [3]string
team[0] = "hammer"
team[1] = "soldier"
team[2] = "mum"
for k, v := range team {
    fmt.Println(k, v)
}
```

```go
0 hammer
1 soldier
2 mum
```

### 赋值

只要类型一致，就可以将多维数组互相赋值

```go
// 声明两个二维整型数组
var array1 [2][2]int
var array2 [2][2]int
array1 = array2
// 将 array1 的索引为 1 的维度复制到一个同类型的新数组里
var array3 [2]int = array1[1]
```

### 切片

[开始位置,结束位置]但不包括结束位置的值

从数组或切片生成新的切片拥有如下特性：

- 取出的元素数量为：结束位置 - 开始位置；
- 取出元素不包含结束位置对应的索引，切片最后一个元素使用 slice[len(slice)] 获取；
- 当缺省开始位置时，表示从连续区域开头到结束位置；
- 当缺省结束位置时，表示从开始位置到整个连续区域末尾；
- 两者同时缺省时，与切片本身等效；
- 两者同时为 0 时，等效于空切片，一般用于切片复位。

```go
a := []int{1, 2, 3}
fmt.Println(a[0:0])
[]
```

#### 切片声明

var name []Type

```go
// 声明字符串切片
var strList []string
// 声明整型切片
var numList []int
// 声明一个空切片
var numListEmpty = []int{}
// 输出3个切片
fmt.Println(strList, numList, numListEmpty)
// 输出3个切片大小
fmt.Println(len(strList), len(numList), len(numListEmpty))
// 切片判定空的结果
fmt.Println(strList == nil)
fmt.Println(numList == nil)
fmt.Println(numListEmpty == nil)
[] [] []
0 0 0
true
true
false
```

#### 使用make()函数构造切片

make( []Type, size, cap )

其中 Type 是指切片的元素类型，size 指的是为这个类型分配多少个元素，cap 为预分配的元素数量，这个值设定后不影响 size，只是能提前分配空间，降低多次分配空间造成的性能问题。

```go
a := make([]int, 2)
b := make([]int, 2, 10)
fmt.Println(a, b)
fmt.Println(len(a), len(b))
[0 0] [0 0]
2 2
```
其中 a 和 b 均是预分配 2 个元素的切片，只是 b 的内部存储空间已经分配了 10 个，但实际使用了 2 个元素。
容量不会影响当前的元素个数，因此 a 和 b 取 len 都是 2。  

使用 make() 函数生成的切片一定发生了内存分配操作，但给定开始与结束位置（包括切片复位）的切片只是将新的切片结构指向已经分配好的内存区域，设定开始与结束位置，不会发生内存分配操作。

#### 使用append()为切片添加元素

```go
var a []int
a = append(a,1);
a = append(a,1,2,3)
a = append(a,[]int{1,2,3,4}...)
fmt.Println(a)
[1 1 2 3 1 2 3 4]
```

  在使用 append() 函数为切片动态添加元素时，如果空间不足以容纳足够多的元素，切片就会进行“扩容”，此时新切片的长度会发生改变。

切片在扩容时，容量的扩展规律是按容量的 2 倍数进行扩充，例如 1、2、4、8、16……

```go
var numbers []int
for i := 0; i < 10; i++ {
    numbers = append(numbers, i)
    fmt.Printf("len: %d  cap: %d pointer: %p\n", len(numbers), cap(numbers), numbers)
}
len: 1  cap: 1 pointer: 0xc0420080e8
len: 2  cap: 2 pointer: 0xc042008150
len: 3  cap: 4 pointer: 0xc04200e320
len: 4  cap: 4 pointer: 0xc04200e320
len: 5  cap: 8 pointer: 0xc04200c200
len: 6  cap: 8 pointer: 0xc04200c200
len: 7  cap: 8 pointer: 0xc04200c200
len: 8  cap: 8 pointer: 0xc04200c200
len: 9  cap: 16 pointer: 0xc042074000
len: 10  cap: 16 pointer: 0xc042074000
```

在开头添加

```go
var a = []int{1,2,3}
a = append([]int{0}, a...) // 在开头添加1个元素
a = append([]int{-3,-2,-1}, a...) // 在开头添加1个切片
```

在中间添加

```go
var a []int
a = append(a[:i], append([]int{x}, a[i:]...)...) // 在第i个位置插入x
a = append(a[:i], append([]int{1,2,3}, a[i:]...)...) // 在第i个位置插入切片
```

#### 切片复制

copy(slice1,slice2) 将slice2复制到slice1，函数将返回成功复制的元素的个数，等于两个 slice 中较小的长度，所以我们不用担心覆盖会超出目标 slice 的范围。



