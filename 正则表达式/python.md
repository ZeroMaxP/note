# 正则匹配

## re.search()

```python
import re#正则模块

# regular expression
pattern1 = "cat"
pattern2 = "bird"
string = "dog runs to cat"
print(re.search(pattern1, string))  # <_sre.SRE_Match object; span=(12, 15), match='cat'>
print(re.search(pattern2, string))  # None
```

### 灵活匹配

### 从中选取一个 [ ]

```python
# multiple patterns ("run" or "ran")
ptn = r"r[au]n"       # start with "r" means raw string
print(re.search(ptn, "dog runs to cat"))   
<_sre.SRE_Match object; span=(4, 7), match='run'>

print(re.search(r"r[A-Z]n", "dog runs to cat"))     
print(re.search(r"r[a-z]n", "dog runs to cat"))     
print(re.search(r"r[0-9]n", "dog r2ns to cat"))     
print(re.search(r"r[0-9a-z]n", "dog runs to cat"))


None
<_sre.SRE_Match object; span=(4, 7), match='run'>
<_sre.SRE_Match object; span=(4, 7), match='r2n'>
<_sre.SRE_Match object; span=(4, 7), match='run'>
```

### 特殊匹配类型

除了自己定义规则, 还有很多匹配的规则时提前就给你定义好了的. 下面有一些特殊的匹配类型给大家先总结一下, 然后再上一些例子.

- \d : 任何数字
- \D : 不是数字
- \s : 任何 white space, 如 [\t\n\r\f\v]
- \S : 不是 white space
- \w : 任何大小写字母, 数字和 “*” [a-zA-Z0-9*]
- \W : 不是 \w
- \b : 空白字符 (**只**在某个字的开头或结尾)
- \B : 空白字符 (**不**在某个字的开头或结尾)
- \\ : 匹配 \
- . : 匹配任何字符 (除了 \n)
- ^ : 匹配开头
- $ : 匹配结尾
- ? : 前面的字符可有可无

```python
# \d : decimal digit
print(re.search(r"r\dn", "run r4n"))           
# <_sre.SRE_Match object; span=(4, 7), match='r4n'>

# \D : any non-decimal digit
print(re.search(r"r\Dn", "run r4n"))           
# <_sre.SRE_Match object; span=(0, 3), match='run'>

# \s : any white space [\t\n\r\f\v]
print(re.search(r"r\sn", "r\nn r4n"))          
# <_sre.SRE_Match object; span=(0, 3), match='r\nn'>

# \S : opposite to \s, any non-white space
print(re.search(r"r\Sn", "r\nn r4n"))          
# <_sre.SRE_Match object; span=(4, 7), match='r4n'>

# \w : [a-zA-Z0-9_]
print(re.search(r"r\wn", "r\nn r4n"))          
# <_sre.SRE_Match object; span=(4, 7), match='r4n'>

# \W : opposite to \w
print(re.search(r"r\Wn", "r\nn r4n"))          
# <_sre.SRE_Match object; span=(0, 3), match='r\nn'>

# \b : empty string (only at the start or end of the word)
print(re.search(r"\bruns\b", "dog runs to cat"))    
# <_sre.SRE_Match object; span=(4, 8), match='runs'>

# \B : empty string (but not at the start or end of a word)
print(re.search(r"\B runs \B", "dog   runs  to cat"))  
# <_sre.SRE_Match object; span=(8, 14), match=' runs '>

# \\ : match \
print(re.search(r"runs\\", "runs\ to me"))     
# <_sre.SRE_Match object; span=(0, 5), match='runs\\'>

# . : match anything (except \n)
print(re.search(r"r.n", "r[ns to me"))         
# <_sre.SRE_Match object; span=(0, 3), match='r[n'>

# ^ : match line beginning
print(re.search(r"^dog", "dog runs to cat"))   
# <_sre.SRE_Match object; span=(0, 3), match='dog'>

# $ : match line ending
print(re.search(r"cat$", "dog runs to cat"))   
# <_sre.SRE_Match object; span=(12, 15), match='cat'>

# ? : may or may not occur
print(re.search(r"Mon(day)?", "Monday"))       
# <_sre.SRE_Match object; span=(0, 6), match='Monday'>

print(re.search(r"Mon(day)?", "Mon"))         
# <_sre.SRE_Match object; span=(0, 3), match='Mon'>
```

