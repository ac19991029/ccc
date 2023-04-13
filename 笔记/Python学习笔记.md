

# **python**

# Python中的短路运算和运算符优先级

## 短路逻辑的核心思想

**从左往右，只有当第一个操作数的值无法确定逻辑运算的结果时，才对第二个操作数进行求值。**

# 运算符优先级

**<u>优先级越高越先执行</u>**

| 优先级 | 运算符                                                       | 描述                                         |
| :----- | ------------------------------------------------------------ | -------------------------------------------- |
| 1      | lambda                                                       | lambda表达式                                 |
| 2      | if-else                                                      | 条件表达式                                   |
| 3      | or                                                           | bool 或                                      |
| 4      | and                                                          | bool 与                                      |
| 5      | not x                                                        | bool 非                                      |
| 6      | int，not int，is，is not，<,<=,>,>=,!=,==                    | 成员测试，同一性测试；比较                   |
| 7      | \|                                                           | 按位或                                       |
| 8      | ^                                                            | 按位异或                                     |
| 9      | &                                                            | 按位与                                       |
| 10     | <<,>>                                                        | 移位                                         |
| 11     | +，-                                                         | 加法，减法                                   |
| 12     | *,@,/,#,%                                                    | 乘法，矩阵乘法，除法，地板除，取余           |
| 13     | +x，-x，~x                                                   | 正号，负号，按位翻转                         |
| 14     | **                                                           | 指数                                         |
| 15     | await x                                                      | await 表达式                                 |
| 16     | x[index],x[index:index],x(arguments...).x.attribute          | 下标，切片，函数调用，属性引用               |
| 17     | (expressions...),[expressions...],{key:value...},{expressions...} | 绑定或元组显示，列表显示，字典显示，集合显示 |



# 列表

## 增

1：append() 在列表末尾增加一个指定元素。

```python
例 number=["1","2"]

增: number.append("3")
```

每次只能添加一个元素

2: extend()：增加一个可迭代对象

```python
例 number=["1","2"]

增：number.extend(["3","4","5"])
```

注：extend()方法的参数必须是一个可迭代对象，新的内容是追加一个到原列表最后一个元素的后面。

3.使用切片：在末尾加

```python
s=[1,2,3,4,5]
s[len(s):]=[6]
s[len(s):]=[7,8,9]
```

4：insert(a,b)方法：a表示插入的位置。b表示插入的数值

```python
s=[1,3,4,5]
s.insert(1,2)
s.insert(0,0)#表示插入到最前面
s.insert(len(s),6)#表示插入到最后 相当于append()方法
```

## 删

1.remove()方法:删除指定元素

```python
s=[1,2,3,4,5]
s.remove(1)
```

#若有多个元素，只删除第一个；若指定元素不存在则报错

2.pop()方法：删除指定下标元素

```python
s=[1,2,3,4,5]
s.pop(2)#即删除下标为2的数即3
```

3.clear()：删除所有元素

```python
s=[1,2,3,4,5]
s.clear()#把列表元素全部删除
```

## 改

```python
s=[1,2,3,4,5]
s[3]=6#将下标3的元素替换即将4替换成6
```

利用切片切换多个元素

```python
s=[1,2,3,4,5]
s[3:]=[7,8]#将4，5替换成7，8
```

sort()排序方法，将乱序排成从小到大

reverse()：从大到小

```python
s=[4,6,32,8,9,6,8,9,6,4]
s.sort(reverse=True)#先排序在翻转
```

## 查

1:count()

```python
s=[4,6,32,8,9,6,8,9,6,4]
s.count(6)#找出共有多少6
```

2:index():查找索引值为多少

```python
s=[4,6,32,8,9,6,8,9,6,4]
s.index(32)#查找元素32的索引值
```

将某个不知道索引值的元素替换

```python
s=[4,6,32,8,9,6,8,9,6,4]
s[s.index(32)]=11#将32元素替换成11
```

3.index():指定查找的开始和结束位置

```python
s=[4,6,32,8,9,6,8,9,6,4]
s.index(9,1,7)#查找9元素 从第一个下标到第七个下标即查找出4
```

## 浅拷贝

1：cpoy()拷贝一个列表

```python
s=[4,6,32,8,9,6,8,9,6,4]
s_copy=s.copy()
```

使用切片方法

```python
s=[4,6,32,8,9,6,8,9,6,4]
s_copy=s[:]
```

copy和切片方式都是浅拷贝，只适用于一维列表

## 深拷贝

```python
import copy
x=[[1,2,3],[4,5,6],[7,8,9]]
y=copy.copy(x)#实现浅拷贝
```

```python
import copy
x=[[1,2,3],[4,5,6],[7,8,9]]
y=copy.deepcopy(x)#深拷贝
```



## 列表的加法和乘法

加法即拼接即可

```python
s=[1,2,3]
t=[4,5,6]
m=s+t
```

乘法  将列表内元素重复

## 嵌套列表

```python
s=[[1,2,3],[4,5,6],[7,8,9]]
```

## 访问嵌套列表

用循环来实现

```python
s=[[1,2,3],[4,5,6],[7,8,9]]
for i in s:
	for each in i:
		print(each)
```

#二维列表

```python
A=[0]*3
for i in range(3):
	A[i]=[0]*3
```

 实现嵌套列表时不能采用直接乘的方式，原因在于这种方法相当于对一个一维列表复制了三次而已。

## 列表推导式

[expression for target in iterable]

```python
s=[1,2,3,4,5,6]
s=[i*2 for i in s]#将每个元素变为原来二倍
```

```python
s=[[1,2,3],[4,5,6],[7,8,9]]
ccc=[row[1] for row i s]#即将每一行的第二个元素提取出来放到ccc里，即[2,5,8]
```

```python
s=[[1,2,3],[4,5,6],[7,8,9]]
diag=[s[i][i] for i in range(len(s))]#提出主对角线元素
```

```python
s=[[9]*3 for i in range(3)]#创建二维列表
```

[expression for target in iterable if condition] 后面可以加一个if条件式

## 元组

#(元素1,元素2,元素3)

```python
nums=(1,2,3,4,5,4,3,2,1,3,4,5)
nums.count(3)#数3有几个
s=(2,3,4,5,6)
d.index(3)#找元素3的下标
d=(2,3,4)
m=(5,6,7)
d+m#嵌套
d*3 #重复三次元素
w=d,m#嵌套
for each in d:
    print(each)#嵌套循环
for i in w:
    for each in i:
        print(each)
a=(1,2,3,4,5)
[each*2 for each in a]#乘2

```

```python
x=(321,)#生成一个只有一个元素的元组
type(x)#查看元素类型
```

## 打包和解包

```python
s=(1,"sdas",3.21)#将不同类型打包
x,y,z=t#将其解包
```

# 字符串

```python
x="Accc"
x.capitalize()#将第一个字母变成大写，剩下的变为小写
x.casefold()#返回一个所有字母都为小写的字符串
x.title()#每个单词的首字母变为大写，其余变为小写
x.swapcase()#将所有字母大小写翻转
x.upper()#将所有字母变为大写
x.lower()#将所有字母变成小写
```

```python
x="有内鬼，终止交易"
x.center(5)#比原字符小，故全部传出
x.center(15)#比原字符大，则左右加空格
x.ljust(15)#左对齐
x.rjust(15)#右对齐
x.zfill(0)#用0填充左侧
```

```python
x="上海自来水来自海上"
x.count("海")#查找出现海的次数
x.count("海"，0,5)#从第一个到第六个字符一共有多少海字
x.find("海")#从左往右找第一个海字的下标
x.rfind("海")#从右往左找第一个海字下标
x.index("贵")#如果找不到抛出异常，find方法则会出-1
table=str.maketrans("abcdefg","1234567")
"I dsa bhdasd djkas".maketrans(table)#将字符串中对应字母替换为数字
```

## 判断

```python
x="我爱python"
x.startswith("我")#判断字符是否在字符串的起始位置
x.endswith("我")#判断字符是否在字符串的结束位置
x.istitle()#判断字符串中是否都为大写字母开头
x.isupper()#判断是否都是大写字母
x.islower()#小写
x.isalpha()#判断是否都为字母构成
x.isspace()#判断是否为空白字符串
x.isprintable()#判断是否可以打印
x.isdecimal()#判断是否为十进制
x.isdigit()#判断是否只有数字组成
x.isnumeric()#判断是否只包含数字字符
x.isalnum()#至少有一个字符并且所有字符都是字母或数字
x.isidentifier()#判断字符串是否是一个合法的python标识符
```

## 截取

```python
x="   左侧不   要留白   "
x.lstrip()#截取掉左侧的空白
x.rstrip()#截取掉右侧
x.strip()#左右侧都截取掉
"www.bing.com".removeprefix("www.")#删除前缀
"www.bing.com".removesuffix(".com")#删除后缀
```

## 拆分和拼接

```python
"www.bing.com".partition(".")#从左到右去找分隔符然后将分割后的分成一割三元组
"www.bing.com".rpartition(".")#从右到左去找分隔符然后将分割后的分成一割三元组
"www.bing.com".split()#默认情况下切分空格
"www.bing.com".rsplit(".")#从右到左分
"www.bing.com".split(".")#从左到右分
"www.bing.com".split("."，1)#从左到右切一刀
"www\nbing\ncom".splitlines()#按行切，并将值返回到列表中
".".join(["www","bing","com"])#将字符串用.分割
```

## 格式化字符串

```python
year=2008
"北京奥运会在{}年举办".format(year)
"{},{{}},{}".format(1,2)#结果"1,{},2"
"{:^10}".format(555)#给出十个字符长度。将555居中 
"{1:>10}{0:<10}".format(555,666)#结果666555居中
"{:010}".format(555)#填充0在555前#只对数字有效，可以填充别的字符
"{:+}{:-}".format(555,-666)#'+555 -666'
"{:,}".format(123456789)#做千分位分隔符结果 123,456,789
"{:.2f}".format(3.1415926)#3.14
"{:2g}".format(3.1415926)#3.1 小数点前后一共2位数
"{:.6}".format("dsalkjdka")#截取前六位
```

| 值     | 含义                                                         |
| ------ | ------------------------------------------------------------ |
| 'b'    | 将参数以二进制输入                                           |
| 'c'    | 将参数以Unicode字符输入                                      |
| 'd'    | 将参数以十进制输入                                           |
| 'o'    | 将参数以八进制输入                                           |
| 'x'    | 将参数以十六进制输入                                         |
| 'X'    | 将参数以十六进制输入                                         |
| 'n'    | 跟'd'类似，不同之处在于他会使用当前语言环境设置的分隔符插入到恰当的位置 |
| 'None' | 跟'd'一样                                                    |

## f-字符串

```python
year=2008
F"北京奥运会在{year}年举办"
f"{-555:010}"
```

# 序列

## 列表、元组和字符串相互转换

```python
list("ccc")
list((1,2,3,4,5))#元组变列表
tuple([1,2,3,4,5])#列表变元组
str([1,2,3,4])#列表变字符串
s=[1,2,3,4,5]
min(s)#找出最小的
max(s)#找出最大的
s=[3,1,23,4,5]
sorted(s)#排序且原来的列表不会改变
sorted(s,reverse=True)#排序翻转
s=['ccc','dasdas','dasa','saqer','eqwxa']
sorted(s)
sort(s,key=len)#调用len函数，比较长度
s=[1,2,3,4,2]
reversed(s)#返回的是一个反向迭代器
list(reversed(s))#显示结果
s=[312,3,2,1,]
all(s)#判断所有元素是否为真
any(s)#
s=[1,2,3,4,5]
enumerate(s)#为每个元素创造一个枚举对象
list(enumerate(s))#将每个元素与序号组成一个元组
#zip()用于创建一个聚合多个可迭代对象的迭代器，将作为参数传入的每个可迭代对象的每个元素一次组成元组，即第i个元组包含来自每个参数的第i个元素。
x=[1,2,3,4,5]
y=['a','b','c','d','e']
zipped=zip(x,y)
list(zipped)#[(1,'a')...]#result
mapped=map(ord,'ccc')
list(mapped)#将'ccc'字符串的Unicode编码转换出
list(filter(str.islower),"ADSCcnbs")#将字符串中的小写字符过滤出来
```



## 迭代器和可迭代对象

一个迭代器肯定是一个可迭代对象

区别：可迭代对象可以重复使用，迭代器是一次性的

```python
x=[1,2,3,4,5]
y=iter(x)#此时y变成一个迭代器
next(y)#将迭代器中的元素一个一个提取出来
```

# 字典

字典是python中唯一实现映射关系的内置类型。

冒号左边是键右边是值

```python
x={"ccc":'1',"bbb":'2'}
x["ddd"]='3'#将不存在的添加进去
a={"ccc":'1',"bbb":'2'}
b=dict(ccc='1',bbb='2')#不能再键上加引号
c=dict([("ccc",'1'),("bbb",'2'),("ddd",'3')])
d=dict({"ccc":'1',"bbb":'2'})
e=dict({"ccc":'1',"bbb":'2'},ddd='3')
f=dict(zip(["ccc","bbb","ddd"],['1','2','3']))#创建字典的方法

```

## 增

```python
x=dict.fromkeys("abc",1)#从无到有创建字典
x['c']=2#改c的键值
x['e']=3#加一个键和键值
```

## 删

```python
x=dict.fromkeys("abc",1)
x.pop('a')#删除a
x.pop('d',"no")#若没有这个键，则抛出异常no
x.popitem()#删除最后一个加入的字典值
del x['b']#删除指定元素
x.clear()#删除字典中所有键和键值
```

## 改

```python
x=dict.fromkeys("abc",None)
x['a']=1#改a的键值
x.update({'c':1,'a':2})#改多个键值，相当于用另一个字典替换里面的内容
x.update(b='3')
```

## 查

```python
x=dict.fromkeys("abc",1)
x['a']#查a键值
x.get('d',"no")#若没有则抛出异常no
x.setdefault('a',"code")#查找并给出键值
x.setdefault('d',"code")#若没有的话，则再字典中加入这个键和键值
#items() keys()  values()分别获取字典的键值对，键 ，键值的视图对象#视图对象即字典的动态视图，即字典的内容发生改变时，视图对象的内容也会相应的进行改变。
keys=x.keys()
values=x.values()
items=x.items()
x.pop('d')#将加入的d弹出
keys=x.keys()
values=x.values()
items=x.items()#视图中内容也相应改变
m=x.copy()#拷贝
len(x)#长度
'a' in x #a是否存在再字典中
list(x)#列表
list(x.values())#键值
z=iter(x)#将字典的键构成迭代器
next(z)#一个一个显示出来
list(reversed(x.values()))#排序
```

## 嵌套

```python
x={"aaa":{"english":60,"math":70},"bbb":{"english":55,"math":90}}
x["aaa"]["english"]#先找aaa再找他的数学成绩
#字典推导式
x={'a':1,'b':2,'c':3}
z={v:k for k,v in x.items()}#将键和键值进行调换
q={v:k for k,v in x.items() if v>50}
x={c:ord(c) for c in "abc"}#将abc每个字符的编码求出来直接
```

# 集合

```python
set([1,1,2,3,4])#去重
s=[1,1,2,3,4]
len(s)== len(set(s))#判断一个元素是否是唯一的
t=s.copy()#浅拷贝
s=set([1,1,2,3,4])
s.isdisjoint(set("python"))#判断两个集合是否相关
s.issubset(set([1,1,2,3,4,5,6]))判断是否是一个集合的子集
s.issuperset(set([1.1]))#判断是否是一个集合的超集
s.union({1,2,3})#构成并集
s.intersection({1,2,3})#求交集
s.difference({1,2,3,4})#求差集
#对称差集，就是除去a和b中的元素共有的元素后剩下的元素
s.symmetric_diffenence({1,2,3,6})
```

```python
s=forzenset([1,2,3,4,5])#集合不可改
s=set("abcd")
s.update([1,1],"23")#将123放入
s.intersection_update("123")#求交集
s.difference_update("cdkl","dsadd")#求差集
s.symmetric_difference_update("ddaslk")#求对称差集
s.add("45")#插入元素，将整个字符串直接插入，而不是分开
s.remove("45")#有则删除 没有则抛出异常
s.discard("45")#删除若没有则静默处理
s.pop()#随机弹出一个元素
s.clear()#清空
```

## 可哈希

如果一个对象是可哈希的，那么他的哈希值必须在其整个程序的生命周期中保持不变,python中可变的对象不可哈希，不可变的对象可哈希

```python
hash(1)#1
hash(1.0)#1
嵌套集合
x={1,23,4}
x=frozenset(x)
y={x,7,8}#{{1,23,4},7,8}
```

# 函数

```python
def myfunc():
	pass
myfunc()#调用函数
def myfunc():
    for i in range(3):
        print("abcdefg")
myfunc()#将abcdefg打印三次
def myfunc(name):
    for i in range(3):
        print(f"abcd{name}")
myfunc("efg")#打印指定参数
```

## 参数

```python
def myfunc(name,times):
    for i in range(times):
        print(f"abcd{name}")
myfunc("efg",5)#指定多个参数
def div(x,y):
    if y==0:
        return "this is none"
    else:
        return x/y
div(3,1)#用return返回结果
```

### 位置参数

```python
def myfunc(s,vt,o):
    return "".join((o,vt,s))#将输入的值颠倒顺序
```

### 关键字参数

```python
def myfunc(s,vt,o):
    return "".join((o,vt,s))#将输入的值颠倒顺序
myfunc(o='1',vt='2',s='3')#设定关键字 则顺序不会改变
位置参数必须再关键字参数之前
```

### 默认参数

```python
def myfunc(s,vt,o='1'):
    return "".join((o,vt,s))
myfunc('2','3')#输出123
默认参数必须放到后面
```

### 收集参数

```python
def myfunc(*args):
    print("有{}个参数".format(len(agrs)))
    print("第2个参数是".format(args[1]))
myfunc("1","22")
def myfunc(*args,a,b):
    print(args,a,b)
myfunc(1,2,3,a=4,b=5)#将123打包成元组，只可以有一个位置参数，剩下的必须为关键字参数
def myfunc(**kwargs):
    print(kwargs)#变成字典
myfunc(a=1,b=2,c=3)#{'a':1,'b':2,'c':3}
def myfunc(a,*b,**c):
    print(1,2,3,4,x=5,y=6)#1是位置参数，234是组成元组，56为字典
```

### 解包参数

```python
args=(1,2,3,4)
def myfunc(a,b,c,d):
    print(a,b,c,d)
myfunc(*args)#将其解包传入abcd四个形参里面
kwargs={'a':1,'b':2,'c':3,'d':4}
myfunc(**kwargs)#将字典解包然后传入abcd四个形参里面
```

## 作用域

### 局部作用域

```python
def myfunc():
	x=520
	print(x)
myfunc()#结果520
变量在函数里面设定，只允许在函数里面访问
```

全局作用域

```python
x=110
def myfunc():
    print(x)
myfunc()#结果110
局部变量会覆盖全局变量的值
```

### global语句

```python
x=110
def myfunc():
    global x
    x=333
    print(x)
myfunc()#result=333
prinx(x)#此时全局变量被修改为333
```

### 嵌套函数

```python
def funA():
    x=110
    def funB():
        x=333
        print("In funB,x=",x)
    funB()
    print("In funA,x=",x)
funA()#result: In funB,x=333 In funA,x=110
```

### nonlocal语句

```python
def funA():
    x=110
    def funB():
        nonlocal x#修改外层值
        x=333
        print("In funB,x=",x)
    funB()
    print("In funA,x=",x)
funA()#result: In funB,x=333 In funA,x=333
```

### LEGB

L:local 局部作用域

E:Enclosed 嵌套函数的外层函数作用域

G:Global全局作用域

B:Build-in内置作用域

## 闭包

```python
def funA():
    x=333
    def funB():
        print(x)
    return funB
a=funA()
a()#result=880
def power(exp):
    def exp_of(base):
        return base**exp
    return exp_of
a=power(2)
b=power(3)#将power函数作为一个工厂 里面值不同实现的功能不同
------------------------------
def outer():
    x=0
    y=0
    def inner(x1,y1):
        nonlocal x,y
        x+=x1
        y+=y1
        print(f"x={x},y={y})
    return inner
a=outer()
a(1,2)#result=x=1,y=2
a(2,2)#result=x=3,y=4
----------------------------------
```

## 装饰器

```python
import time
def time_master(func):
    print("开始运行程序...")
    start=time.time()
    func()
    stop=time.time()
    print("结束程序运行...")
    print(f"一共耗费了{(stop-start):.2f}秒")
def myfunc():
    time.sleep(2)
    print("Hello world")
time_master(myfunc)#用time_master函数调用myfunc函数
-----------------------------------------
装饰器
import time
def time_master(func):
    def call_func():
        print("开始运行程序...")
        start=time.time()
        func()
        stop=time.time()
        print("结束程序运行...")
        print(f"一共耗费了{(stop-start):.2f}秒")
    return call_func
@time_master
def myfunc():
    time.sleep(2)
    print("Hello world")
myfunc()
---------------------------------------
def add(func):
    def inner():
        x=func()
        return x+1
    return inner
def cube(func):
    def inner():
        x=func()
        return x*x*x
    return inner
def square(func):
    def inner():
        x=func():
            return x*x
        return x*x
    return inner
@add
@cube
@square
def test():
    return 2
print(test())#result 65 先执行square在执行cube在执行add
-------------------------------------------
装饰器传递参数
import time
def longger(msg):
    def time_master(func):
        def call_func():
            start=time.time()
            func()
            stop=time.time()
            print(f"{msg}一共耗费{(stop-start):.2f}")
        return call_func
    return time_master

@longger(msg='A')
def funA():
    time.sleep(1)
    print("正在调用funA...")
@longger(msg='B')
def funB():
    time.sleep(1)
	print("正在调用funB...")
funA()
funB()
```

## lambda表达式

lambda arg1,arg2,arg3...argN:expression	

```python
square=lambda x:x*x
square(3)#result=9
y=[lambda x:x*x,2,3]
y[0](y[1])#result=4
y[0](y[2])#result=9
list(filter(lambda x:x%2),range(10))#result=[1,3,5,7,9]
```







```java
public static void publishTypeBytes(String streamID, byte[] hexData) {
    byte[] idBytes = streamID.getBytes();

    int idLength = idBytes.length;
    int hexLength = hexData.length;
    int payloadLength = idLength+hexLength+7;
    byte[] payload = new byte[payloadLength];

    byte type = (byte) 0x02;               // 上传类型2 json格式
    byte[] idLengthBytes = new byte[]{       // 数据流ID的长度
            (byte) ((idLength >> 8) & 0xFF),   // 高八位
            (byte) (idLength & 0xFF)           // 低八位
    };
    byte[] binLengthBytes = new byte[]{              // 十六进制数据的长度
            (byte) ((hexLength >> 24) & 0xFF),      // 占用四个字节
            (byte) ((hexLength >> 16) & 0xFF),
            (byte) ((hexLength >> 8) & 0xFF),
            (byte) (hexLength & 0xFF)
    };
    payload[0] = type;
    payload[1] = idLengthBytes[0];
    payload[2] = idLengthBytes[1];
    System.arraycopy(idBytes,0,payload,3,idLength);//将数组idBytes拷贝到plyload数组中
    payload[idLength+3] = binLengthBytes[0];
    payload[idLength+3+1] = binLengthBytes[1];
    payload[idLength+3+2] = binLengthBytes[2];
    payload[idLength+3+3] = binLengthBytes[3];
    System.arraycopy(hexData,0,payload,(idLength+3+4),hexLength);
    MQTTService.publish(SYSTEMS_PUBLISH_TOPIC,payload);
}
```

