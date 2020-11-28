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

### 切片





