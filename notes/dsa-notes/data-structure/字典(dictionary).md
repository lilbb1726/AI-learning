---
aliases:
  - dictionary
  - dict
tags:
  - python内置
  - 基本语法
---
# Python Dict 常用语法与复杂度

> 设字典中共有 `n` 个键值对，待添加字典中共有 `k` 个键值对。  
> 字典底层通常使用哈希表，因此查找、插入、修改和删除的平均时间复杂度通常为 $O(1)$。

> ⚠️ 注意  
> 字典操作的 $O(1)$ 通常指平均或摊还时间复杂度。极端哈希冲突情况下，理论最坏复杂度可能退化为 $O(n)$。

---

# 创建字典

## 使用大括号

```python
student = {
    "name": "Tom",
    "age": 20
}
```

- 使用 `key: value` 的形式存储键值对
- 创建含有 `n` 个键值对的字典，时间复杂度为 $O(n)$

---

## 使用 dict()

```python
student = dict(name="Tom", age=20)
```

也可以由键值对序列创建：

```python
student = dict([
    ("name", "Tom"),
    ("age", 20)
])
```

- 返回值：新字典
- 时间复杂度：$O(n)$

---

## 创建空字典

```python
student = {}
```

或者：

```python
student = dict()
```

- 时间复杂度：$O(1)$

---

## 字典的基本特点

- 字典以**键值对**的形式存储数据
- 键必须唯一
- 值可以重复
- 键必须是可哈希对象
- 字典按照插入顺序保存键值对

可以作为键的常见类型：

```python
str
int
float
tuple
```

不能直接作为键的常见类型：

```python
list
dict
set
```

> ⚠️ 注意  
> 列表、字典和集合属于可变对象，通常不能作为字典的键。

---

# 访问元素

## 使用方括号

根据键访问对应的值。

```python
value = data[key]
```

- 不修改原字典
- 返回值：键对应的值
- 平均时间复杂度：$O(1)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

print(student["name"])
# Tom
```

> ⚠️ 注意  
> 如果键不存在，会产生 `KeyError`。

```python
student["score"]
# KeyError: 'score'
```

---

## get()

获取指定键对应的值。

```python
value = data.get(key)
```

也可以指定键不存在时的默认返回值：

```python
value = data.get(key, default)
```

- 不修改原字典
- 返回值：键对应的值，或者默认值
- 平均时间复杂度：$O(1)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

print(student.get("age"))
# 20

print(student.get("score"))
# None

print(student.get("score", 0))
# 0
```

### 方括号与 get() 的区别

```python
data[key]
```

- 键存在：返回对应值
- 键不存在：产生 `KeyError`

```python
data.get(key, default)
```

- 键存在：返回对应值
- 键不存在：返回默认值
- 不会产生 `KeyError`

---

# 添加与修改元素

## 使用方括号赋值

```python
data[key] = value
```

- 键不存在：添加新的键值对
- 键已存在：修改原来的值
- 修改原字典
- 返回值：无
- 平均或摊还时间复杂度：$O(1)$

示例：

```python
student = {
    "name": "Tom"
}

student["age"] = 20
# 添加新的键值对

student["name"] = "Jack"
# 修改已有键对应的值

print(student)
# {'name': 'Jack', 'age': 20}
```

> ⚠️ 注意  
> 字典的键不能重复。对同一个键重新赋值，会覆盖原来的值。

---

## update()

使用另一个字典或键值对集合更新当前字典。

```python
data.update(other)
```

- 修改原字典
- 返回值：`None`
- 平均时间复杂度：$O(k)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

student.update({
    "age": 21,
    "score": 95
})

print(student)
# {'name': 'Tom', 'age': 21, 'score': 95}
```

> ⚠️ 注意  
> 如果新字典中含有相同的键，原来的值会被覆盖。

---

## setdefault()

获取指定键对应的值；如果键不存在，则添加该键和默认值。

```python
value = data.setdefault(key, default)
```

- 键存在：返回原来的值，不修改字典
- 键不存在：添加 `key: default`
- 平均时间复杂度：$O(1)$

示例：

```python
student = {
    "name": "Tom"
}

age = student.setdefault("age", 20)

print(age)
# 20

print(student)
# {'name': 'Tom', 'age': 20}
```

当键已经存在时：

```python
student = {
    "age": 18
}

age = student.setdefault("age", 20)

print(age)
# 18

print(student)
# {'age': 18}
```

### get() 与 setdefault() 的区别

```python
data.get(key, default)
```

- 键不存在时只返回默认值
- 不会修改原字典

```python
data.setdefault(key, default)
```

- 键不存在时返回默认值
- 同时把该键值对加入字典

---

# 删除元素

## pop()

根据键删除键值对，并返回被删除的值。

```python
value = data.pop(key)
```

- 修改原字典
- 返回值：被删除键对应的值
- 平均时间复杂度：$O(1)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

age = student.pop("age")

print(age)
# 20

print(student)
# {'name': 'Tom'}
```

> ⚠️ 注意  
> 如果键不存在且没有设置默认值，会产生 `KeyError`。

也可以设置默认值：

```python
value = data.pop(key, default)
```

示例：

```python
student = {
    "name": "Tom"
}

result = student.pop("age", 0)

print(result)
# 0
```

---

## del

根据键删除键值对。

```python
del data[key]
```

- 修改原字典
- 返回值：无
- 平均时间复杂度：$O(1)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

del student["age"]

print(student)
# {'name': 'Tom'}
```

> ⚠️ 注意  
> 如果键不存在，会产生 `KeyError`。

---

## popitem()

删除并返回最后插入的键值对。

```python
item = data.popitem()
```

- 修改原字典
- 返回值：由 `(key, value)` 组成的元组
- 平均时间复杂度：$O(1)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

item = student.popitem()

print(item)
# ('age', 20)

print(student)
# {'name': 'Tom'}
```

> ⚠️ 注意  
> `popitem()` 删除的是最后插入的键值对。  
> 如果字典为空，会产生 `KeyError`。

---

## clear()

清空字典中的所有键值对。

```python
data.clear()
```

- 修改原字典
- 返回值：`None`
- 时间复杂度：$O(n)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

student.clear()

print(student)
# {}
```

---

## pop() 与 del 的区别

```python
value = data.pop(key)
```

- 删除键值对
- 返回被删除的值
- 可以设置默认返回值

```python
del data[key]
```

- 删除键值对
- 不返回被删除的值
- 不能设置默认值

---

# 查找键

## in

判断指定键是否存在于字典中。

```python
key in data
```

- 判断的是键，不是值
- 返回值：`True` 或 `False`
- 平均时间复杂度：$O(1)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

print("name" in student)
# True

print("Tom" in student)
# False
```

> ⚠️ 注意  
> `in` 默认检查字典的键。

```python
"name" in student
```

等价于：

```python
"name" in student.keys()
```

---

## not in

判断指定键是否不存在于字典中。

```python
key not in data
```

- 返回值：`True` 或 `False`
- 平均时间复杂度：$O(1)$

---

## 查找值

如果需要判断某个值是否存在：

```python
value in data.values()
```

- 返回值：`True` 或 `False`
- 时间复杂度：$O(n)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

print("Tom" in student.values())
# True
```

> ⚠️ 注意  
> 根据键查找通常是 $O(1)$，但根据值查找需要逐个检查，因此是 $O(n)$。

---

# 获取键、值和键值对

## keys()

获取字典中的所有键。

```python
keys = data.keys()
```

- 不修改原字典
- 返回值：动态视图对象
- 创建视图的时间复杂度：$O(1)$
- 完整遍历时间复杂度：$O(n)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

print(student.keys())
# dict_keys(['name', 'age'])
```

需要转为列表时：

```python
keys = list(student.keys())
```

- 时间复杂度：$O(n)$
- 额外空间复杂度：$O(n)$

---

## values()

获取字典中的所有值。

```python
values = data.values()
```

- 不修改原字典
- 返回值：动态视图对象
- 创建视图的时间复杂度：$O(1)$
- 完整遍历时间复杂度：$O(n)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

print(student.values())
# dict_values(['Tom', 20])
```

---

## items()

获取字典中的所有键值对。

```python
items = data.items()
```

- 不修改原字典
- 返回值：由 `(key, value)` 组成的动态视图对象
- 创建视图的时间复杂度：$O(1)$
- 完整遍历时间复杂度：$O(n)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

print(student.items())
# dict_items([('name', 'Tom'), ('age', 20)])
```

---

# 遍历字典

## 遍历键

```python
for key in data:
    print(key)
```

等价于：

```python
for key in data.keys():
    print(key)
```

- 完整遍历时间复杂度：$O(n)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

for key in student:
    print(key)
```

输出：

```text
name
age
```

---

## 遍历值

```python
for value in data.values():
    print(value)
```

- 完整遍历时间复杂度：$O(n)$

---

## 同时遍历键和值

```python
for key, value in data.items():
    print(key, value)
```

- 完整遍历时间复杂度：$O(n)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

for key, value in student.items():
    print(key, value)
```

输出：

```text
name Tom
age 20
```

---

# 字典计数器

字典可以用于统计元素出现次数。

```python
counter = {}

for ch in text:
    counter[ch] = counter.get(ch, 0) + 1
```

示例：

```python
text = "banana"
counter = {}

for ch in text:
    counter[ch] = counter.get(ch, 0) + 1

print(counter)
# {'b': 1, 'a': 3, 'n': 2}
```

- 遍历字符串需要 $O(n)$
- 每次字典查询和修改平均为 $O(1)$
- 总时间复杂度：$O(n)$
- 空间复杂度：$O(k)$

其中 `k` 是不同字符的数量。

---

# 字典推导式

根据可迭代对象快速创建字典。

```python
data = {
    key_expression: value_expression
    for item in iterable
}
```

示例：

```python
squares = {
    x: x * x
    for x in range(5)
}

print(squares)
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

- 返回值：新字典
- 时间复杂度：$O(n)$
- 空间复杂度：$O(n)$

带条件：

```python
even_squares = {
    x: x * x
    for x in range(10)
    if x % 2 == 0
}
```

---

# 复制字典

## copy()

创建字典的浅拷贝。

```python
new_data = data.copy()
```

- 不修改原字典
- 返回值：新字典
- 时间复杂度：$O(n)$
- 空间复杂度：$O(n)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

new_student = student.copy()
```

> ⚠️ 注意  
> `copy()` 是浅拷贝。如果字典中的值是可变对象，两个字典仍可能共享内部对象。

---

# 获取字典长度

## len()

获取字典中键值对的数量。

```python
len(data)
```

- 不修改原字典
- 返回值：键值对数量
- 时间复杂度：$O(1)$

示例：

```python
student = {
    "name": "Tom",
    "age": 20
}

print(len(student))
# 2
```

---

# 字典比较

两个字典相等，需要拥有相同的键，并且每个键对应的值也相同。

```python
dict1 == dict2
```

- 字典的插入顺序不影响相等性判断
- 最坏时间复杂度：$O(n)$

示例：

```python
dict1 = {
    "a": 1,
    "b": 2
}

dict2 = {
    "b": 2,
    "a": 1
}

print(dict1 == dict2)
# True
```

---

# 常用操作复杂度汇总

| 操作 | 含义 | 是否修改原字典 | 平均时间复杂度 |
|---|---|---|---:|
| `data[key]` | 根据键访问值 | 否 | $O(1)$ |
| `data.get(key)` | 安全获取值 | 否 | $O(1)$ |
| `data[key] = value` | 添加或修改键值对 | 是 | $O(1)$ |
| `data.update(other)` | 批量添加或修改 | 是 | $O(k)$ |
| `data.setdefault(key, default)` | 获取或添加默认值 | 可能 | $O(1)$ |
| `data.pop(key)` | 删除指定键并返回值 | 是 | $O(1)$ |
| `del data[key]` | 删除指定键 | 是 | $O(1)$ |
| `data.popitem()` | 删除最后插入的键值对 | 是 | $O(1)$ |
| `data.clear()` | 清空字典 | 是 | $O(n)$ |
| `key in data` | 判断键是否存在 | 否 | $O(1)$ |
| `value in data.values()` | 判断值是否存在 | 否 | $O(n)$ |
| `data.keys()` | 获取键视图 | 否 | $O(1)$ |
| `data.values()` | 获取值视图 | 否 | $O(1)$ |
| `data.items()` | 获取键值对视图 | 否 | $O(1)$ |
| `for key in data` | 遍历所有键 | 否 | $O(n)$ |
| `for value in data.values()` | 遍历所有值 | 否 | $O(n)$ |
| `for key, value in data.items()` | 遍历所有键值对 | 否 | $O(n)$ |
| `len(data)` | 获取键值对数量 | 否 | $O(1)$ |
| `data.copy()` | 浅拷贝字典 | 否 | $O(n)$ |
| `dict1 == dict2` | 判断两个字典是否相等 | 否 | 最坏 $O(n)$ |

---

# Dict 与 [[列表(list)|List]] 的简单对比

| 特点 | List | Dict |
|---|---|---|
| 存储方式 | 按位置存储元素 | 按键存储值 |
| 访问方式 | 通过下标访问 | 通过键访问 |
| 随机访问 | $O(1)$ | 平均 $O(1)$ |
| 判断元素是否存在 | $O(n)$ | 判断键平均 $O(1)$ |
| 是否保持插入顺序 | 是 | 是 |
| 键或下标是否唯一 | 下标唯一 | 键唯一 |
| 常见用途 | 有序数据、栈、序列 | 映射、查找、计数器、哈希表 |

> 我的理解：  
> `list` 通过下标定位元素，适合按顺序存储数据；`dict` 通过键的哈希值定位数据，适合快速查找、映射和计数。