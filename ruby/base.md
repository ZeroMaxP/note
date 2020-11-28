### 运行

1. `irb` 来编写程序
2. 保存为`name.rb` 使用ruby name.rb 运行
3. 开头填写的#!/uer/bin/env ruby -w(w是开启警告) utf-8



### 注释用# #

``` ruby
#注释

=begin
多行注释
多行注释
多行注释
多行注释
=end
```



### 运算符

`**` 是幂运算

`(..),(...)` 是范围运算符

```ruby
puts(5**2)
25

puts(1..5)
1,2,3,4,5

pust(1...5)
1,2,3,4
```



### 输出

程序会原封不动地输出单引号里的内容。

方法调用可以省略括号

> print <<`str` 以str作为结束符,中间的内容将会被输出,puts可以自动换行

```ruby
puts 'hemmlw\n'
hemmlw\n
=> nil

print "hemmlw\n"
hemmlw
=> nil


print <<EOF
	hellow 
	world
EOF

print <<`EOF`  #` `可以使用命令
	echo hellow
EOF

print <<`EOF`,  <<"eof"
	echo hellow
EOF
	echo hellowworld
	 hi
eof

	hellow 
	world
hellow
hellow
	echo hellowworld
	 hi

```

### BEGIN

> 这段代码会在程序执行前调用

```ruby
BEGIN{
    code
}
```



### END

>这段代码会在程序执行结尾被调用

```ruby
END{
	code    
}
```

#### demo

```ruby
END{
	puts 'end'
}
BEGIN{
	puts 'begin'
}

begin
end
```



### 数据类型

```ruby

```





### if condition

```ruby
if express
    program
elsif express2
    program
end

```
`不支持switch ,case`

