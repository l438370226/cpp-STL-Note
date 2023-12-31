# STL

## 容器

### string

#### string构造函数

```c++
string();		//创建一个空字符串
string(const char *s);		//使用字符串s初始化
string(const string &str);		//使用string对象初始化
string(int n, char c);		//使用n个字符c初始化
```

#### string赋值操作

```c++
string& operator=(const char *s);
string& operator=(const string &s);
string& operator=(char c);
string& assign(const char *s);
string& assign(const char*s, int n);		//赋值为字符串s前n个字符
string& assign(const string &s);
string& assign(int n, char c);		//赋值为n个字符c
```

#### string常用接口

##### 拼接

```c++
string& operator+=(const char *str);		//+=重载
string& operator+=(const char c);		//+=重载
string& operator+=(const string &str);		//+=重载
string& append(const char *s);
string& append(const char *s, int n);		//将字符串s前n个字符拼接到字符串结尾
string& append(const string &s);
string& append(const string &s, int pos, int n);		//将string对象s从pos开始n个字符拼接到字符串结尾
```

##### 查找

```c++
int find(const string &str, int pos=0) const;		//查找str第一次出现位置，从pos查找
int find(const char *s, int pos=0) const;
int find(const char *s, int pos, int n) const;		//查找s前n个字符第一次出现位置，从pos查找
int find(const char c, int pos=0) const;
int rfind(const string &str, int pos=npos) const;		//查找str最后一次出现位置，从pos查找
int rfind(const char *s, int pos=npos) const;
int rfind(const char *s, int pos, int n) const;
int rfind(const char c, int pos=0) const;
```

##### 替换

```c++
string& replace(int pos, int n, const string& str);		//替换pos开始n个字符为字符串str
string& replace(int pos, int n, const char *s);
```

##### 比较

```c++
int compare(const string &s) const;		//=返回0，>返回1，<返回-1
int compare(const char *s) const;
```

##### 存取

```c++
char& operator[](int n);		//[]重载
char& at(int n);		//通过at()方法
```

##### 插入

```c++
string& insert(int pos, const char *s);
string& insert(int pos, const string &str);
string& insert(int pos, int n, char c);		//在指定位置pos插入n个字符c
```

##### 删除

```c++
string& erase(int pos, int n=npos);		//删除从pos开始n个字符
```

##### 子串

```c++
string substr(int pos=0, int n=npos) const;		//返回pos开始n个字符组成的字符串
```



### vector

#### vector构造函数

```c++
vector<T> v;		//采用模板实现，默认构造函数
vector(v.begin(), v.end());		//将v[begin(),end())区间中元素拷贝
vector(n, elem);		//构造函数将n个elem拷贝
vector(const vector &vec);		//拷贝构造函数
```

#### vector赋值操作

```c++
vector& operator=(const vector &vec);		//重载=
vector& assign(begin, end);
vector& assign(n, elem);
```

#### vector常用接口

##### 容量和大小

```c++
empty();		//判断是否为空
capacity();		//容量大小
size();		//元素个数
resize(int num);		//重新指定容器长度为num，若容器变长，以默认值填充，变短则删除超出部分
resize(int num, elem);		//resize重载，容器变长时以elem填充
```

##### 插入

```c++
push_back(elem);		//尾插
pop_back();		//删除最后一个元素
insert(const_iterator pos, elem);		//迭代器指向位置pos处插入elem
insert(const_iterator pos, int count, elem);		//迭代器指向位置pos处插入count个elem
```

##### 删除

```c++
erase(const_iterator pos);		//删除pos指向元素
erase(const_iterator start, const_iterator end);		//删除start-end之间元素
clear();		//删除所有元素
```

##### 存取

```c++
at(int idx);		//返回idx指向元素
operator[];		//[]重载
front();		//返回第一个元素
back();		//返回最后一个元素
```

##### 互换

```c++
swap(vec);		//vec与本身元素互换
vector<T>(v).swap(v)		//创建匿名对象与自身互换收缩内存
```

##### 预留

```c++
reserve(int len);		//预留len个元素长度，不初始化，不可访问
```



### deque

#### deque构造函数

```c++
deque<T> deq;
deque(begin, end);
deque(n, elem);
deque(const deque &deq);
```

#### deque赋值操作

```c++
deque& operator=(const deque &deq);
deque& assign(begin, end);
deque& assign(n, elem);
```

#### deque常用接口

##### 大小

```c++
empty();
size();
resize(num);
resize(num, elem);
```

##### 插入

```c++
push_back(elem);		//尾插
push_front(elem);		//头插
insert(pos, elem);		//指定位置pos处插入
insert(pos, n, elem);
insert(pos, begin, end);		//在pos处插入[begin,end)元素
```

##### 删除

```c++
pop_back();		//尾删
pop_front();		//头删
erase(pos);
erase(begin, end);
clear();
```

##### 存取

```c++
operator[];
at(int idx);
front();
back();
```



### stack

#### stack构造函数

```c++
stack<T> stk;
stack(const stack &stk);
```

#### stack赋值操作

```c++
stack& operator=(const stack &stk);
```

#### stack常用接口

##### 大小

```c++
empty();
size();
```

##### 存取

```c++
push(elem);
pop();
top();
```



### queue

#### queue构造函数

```c++
queue<T> que;
queue(const queue &que);
```

#### queue赋值操作

```c++
queue& operator=(const queue &que);
```

#### queue常用接口

##### 大小

```c++
empty();
size();
```

##### 存取

```c++
push(elem);		//入队
pop();		//出队
back();		//队尾元素
front();		//队头元素
```



### list		//双向循环链表

#### list构造函数

```c++
list<T> lst;
list(begin, end);
list(n, elem);
list(const list &lst);
```

#### list赋值操作

```c++
list& operator=(const list &lst);
list& assign(begin, end);
list& assign(n, elem);
```

#### list常用接口

##### 大小

```c++
size();
empty();
resize(num);
resize(num, elem);
```

##### 插入

```c++
push_back(elem);
push_front(elem);
insert(pos, elem);
insert(pos, n, elem);
insert(pos, begin, end);
```

##### 删除

```c++
pop_back();
pop_front();
erase(begin, end);
erase(pos);
remove(elem);		//删除容器中所有与elem值匹配的元素
clear();
```

##### 存取

```c++
front();
back();
```

##### 反转

```c++
reverse();
```

##### 排序

```c++
sort();		//成员函数，可指定规则
```

##### 交换

```c++
swap(list);
```



### set/multiset

#### 区别

set不允许有重复元素，multiset允许重复

#### set构造函数

```c++
set<T> st;
set(const set &st);
```

#### set赋值操作

```c++
set& operator=(const set &st);
```

#### set常用接口

##### 大小

```c++
size();
empty();
```

##### 插入

```c++
insert(elem);		//set返回<iterator,bool>数据，multiset返回iterator数据
```

##### 删除

```c++
erase(pos);
erase(begin, end);
erase(elem);
clear();
```

##### 查找

```c++
find(key);		//若存在，返回元素的迭代器，若不存在，返回set.end()
```

##### 统计

```c++
count(key);
```

##### 排序

```c++
set<T,class cls> st;		//利用cls中仿函数指定排序规则
```

##### 交换

```c++
swap(st);
```



### map/multimap

#### 区别

map不允许容器中有重复key值元素，multimap允许存在重复key值元素

#### map构造函数

```c++
map<T1, T2> mp;
map(const map &mp);
```

#### map赋值操作

```c++
map& operator=(const map &mp);
```

#### map常用接口

##### 大小

```c++
size();
empty();
```

##### 插入

```c++
insert(elem);
m[key]=value;		//重载[]，key不存在时插入，未指定value时为0
```

##### 删除

```c++
erase(pos);
erase(begin, end);
erase(key);		//指定key值元素删除
clear();
```

##### 查找

```c++
find(key);
```

##### 统计

```c++
count(key);
```

##### 排序

```c++
map<T1, T2, class cls> mp;		//cls中仿函数指定排序规则
```

##### 交换

```c++
swap(mp);
```



### unordered_map

#### unordered_map构造函数

```c++
unordered_map<T1, T2> ump;
unordered_map(begin, end);
unordered_map(const unordered_map &ump);
unordered_map(unordered_map&& ump);
unordered_map({elemlist})
```

#### unordered_map赋值操作

```c++
unordered_map& operator(const unordered_map &ump);
```

#### unordered_map常用接口

##### 大小

```c++
empty();
size();
max_size();
```

##### 插入

```c++
insert(elem);
insert(Inputlt first, Inputlt last);
insert(ilist);
insert_or_assign(key, value);		//若等价于key的键值已存在，则赋值，否则插入
```

##### 删除

```c++
erase(pos);
erase(begin, end);
erase(key);
clear();
```

##### 查找

```c++
at(key);
T& operator[](key);
find(key);
```

##### 统计

```c++
count(key);
```

##### 交换

```c++
swap(ump)
```



## 内建仿函数

### 算术仿函数

```c++
template<class T> T plus<T>;		//加法
template<class T> T minus<T>;		//减法
template<class T> T multiplies<T>;		//乘法
template<class T> T divides<T>;		//除法
template<class T> T modulus<T>;		//取模
template<class T> T negate<T>;		//取反
```

### 关系仿函数

```c++
template<class T> bool equal_to<T>;
template<class T> bool no_equal_to<T>;
template<class T> bool greater<T>;
template<class T> bool greater_equal<T>;
template<class T> bool less<T>;
template<class T> bool less_equal<T>;
```

### 逻辑仿函数

```c++
template<class T> bool logical_and<T>;
template<class T> bool logical_or<T>;
template<class T> bool logical_not<T>;
```

## 常用算法

### 常用遍历算法

```c++
for_each(iterator begin, iterator end, _func);		//_func为函数或函数对象
transform(iterator begin1, iterator end1, iteratoor begin2, _func);		//begin1原容器开始迭代器，begin2目标容器开始迭代器
```

### 常用查找算法

```c++
find(iterator begin, iterator end, value);		//自定义数据类型需要重载'=='
find_if(iterator begin, iterator end, _Pred);		//_Pred函数或谓词(返回bool类仿函数)
adjacent_find(iterator begin, iterator end);		//查找相邻重复元素
bool binary_search(iterator begin, iterator end, value);		//二分查找，要求有序
count(iterator begin, iterator end, value);
count_if(iterator begin, iterator end, _Pred);
```

### 常用排序算法

```c++
sort(iterator begin, iterator end, _Pred);
random_shuffle(iterator begin, iterator end);		//随机打乱
merge(iterator begin1, iterator end1, iterator begin2, iterator end2, iterator dest);		//两个容器必须有序,合并储存到另一容器，dest为目标容器开始迭代器
reverse(iterator begin, iterator end);
```

### 常用拷贝算法

```c++
copy(iterator begin, iterator end, iterator dest);
```

### 常用替换算法

```c++
replace(iterator begin, iterator end, oldvalue, newvalue);
replace_if(iterator begin, iterator end, _Pred, newvalue);
swap(container c1, container c2);
```

### 常用算数生成算法

```c++
accumulate(iterator begin, iterator end, value);		//value为起始累加值，计算value+区间内元素之和
fill(iterator begin, iterator end, value);
```

### 常用集合算法

```c++
iterator set_intersection(interator begin1, interator end1, interator begin2, interator end2, interator dest);		//求交集,返回交集结束处迭代器
iterator set_union(interator begin1, interator end1, interator begin2, interator end2, interator dest);		//求并集
iterator set_difference(interator begin1, interator end1, interator begin2, interator end2, interator dest);		//求差集
```

