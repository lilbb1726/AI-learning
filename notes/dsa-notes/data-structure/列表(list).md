---
aliases:
  - list
tags:
  - 基本语法
  - python内置
---
# Python List 常用语法与复杂度

> 设原列表长度为 `n`，待添加列表或可迭代对象长度为 `k`。

---

# 添加元素

## append()

在列表末尾添加**一个元素**。

```python
nums.append(x)
```

- 修改原列表
- 返回值：`None`
- 时间复杂度：**摊还 O(1)**

示例：

```python
nums = [1, 2]

result = nums.append(3)

print(nums)
# [1, 2, 3]

print(result)
# None
```

> ⚠️ 注意  
> `append()` 添加的是一个整体元素，如果添加列表，会形成嵌套列表。

```python
nums = [1, 2]

nums.append([3, 4])

# [1, 2, [3, 4]]
```

---

## extend()

将一个可迭代对象中的元素**逐个添加**到列表末尾。

```python
nums.extend(other)
```

- 修改原列表
- 返回值：`None`
- 时间复杂度：**O(k)**

示例：

```python
nums = [1, 2]

nums.extend([3, 4])

print(nums)
# [1, 2, 3, 4]
```

### append() 与 extend() 的区别

```python
nums.append([3, 4])

# [1, 2, [3, 4]]
```

将整个列表作为一个元素加入。


```python
nums.extend([3, 4])

# [1, 2, 3, 4]
```

将列表中的元素逐个加入。

---

## insert()

在指定下标 `i` 的位置前插入元素。

```python
nums.insert(i, x)
```

- 修改原列表
- 返回值：`None`
- 时间复杂度：**O(n)**

示例：

```python
nums = [1, 2, 3]

nums.insert(1, 100)

print(nums)
# [1, 100, 2, 3]
```

> ⚠️ 注意  
> 插入位置越靠前，需要移动的元素越多，因此复杂度为 O(n)。

---

# 删除元素

## pop()

删除并返回列表最后一个元素。

```python
nums.pop()
```

- 修改原列表
- 返回值：删除的元素
- 时间复杂度：**O(1)**

示例：

```python
nums = [10, 20, 30]

x = nums.pop()

print(x)
# 30

print(nums)
# [10, 20]
```

---

## pop(i)

删除并返回指定下标 `i` 的元素。

```python
nums.pop(i)
```

- 修改原列表
- 返回值：删除的元素
- 最坏时间复杂度：**O(n)**

示例：

```python
nums = [10, 20, 30, 40]

x = nums.pop(1)

print(x)
# 20

print(nums)
# [10, 30, 40]
```

### pop() 与 pop(i) 的区别

```python
nums.pop()

# 删除最后一个元素
# O(1)
```

```python
nums.pop(i)

# 删除指定位置元素
# 最坏 O(n)
```

> ⚠️ 注意  
> `pop(i)` 删除元素后，需要将后面的元素向前移动。

---

## remove()

删除列表中第一次出现的指定值。

```python
nums.remove(x)
```

- 修改原列表
- 返回值：`None`
- 时间复杂度：**O(n)**

示例：

```python
nums = [1, 2, 3, 2]

nums.remove(2)

print(nums)
# [1, 3, 2]
```

> ⚠️ 注意  
> - 只删除第一次出现的元素
> - 如果元素不存在，会报错

---

## clear()

清空列表。

```python
nums.clear()
```

- 修改原列表
- 返回值：`None`
- 时间复杂度：**O(n)**

---

# 查找元素

## index()

返回指定值第一次出现的下标。

```python
nums.index(x)
```

- 返回值：元素第一次出现的位置
- 时间复杂度：**O(n)**

示例：

```python
nums = [10, 20, 30, 20]

i = nums.index(20)

print(i)
# 1
```

> ⚠️ 注意  
> 如果元素不存在，会报错。

---

## count()

统计指定值出现次数。

```python
nums.count(x)
```

- 返回值：出现次数
- 时间复杂度：**O(n)**

示例：

```python
nums = [1, 2, 2, 3]

print(nums.count(2))
# 2
```

---

## in

判断元素是否存在。

```python
x in nums
```

- 返回值：`True / False`
- 时间复杂度：**O(n)**

示例：

```python
nums = [1, 2, 3]

print(2 in nums)
# True
```

---

# 排序

## sort()

对原列表进行排序。

```python
nums.sort()
```

- 修改原列表
- 返回值：`None`
- 时间复杂度：**O(n log n)**

示例：

```python
nums = [3, 1, 2]

nums.sort()

print(nums)
# [1, 2, 3]
```

> ⚠️ 注意  
> `sort()` 只能用于列表，并且会改变原列表。

---

## sorted()

排序并返回一个新的列表。

```python
new_nums = sorted(nums)
```

- 不修改原列表
- 返回值：新的列表
- 时间复杂度：**O(n log n)**

示例：

```python
nums = [3, 1, 2]

new_nums = sorted(nums)

print(nums)
# [3, 1, 2]

print(new_nums)
# [1, 2, 3]
```

### sort() 与 sorted() 的区别

|方法|是否修改原列表|返回值|
|-|-|-|
|sort()|是|None|
|sorted()|否|新列表|

---

# 翻转

## reverse()

原地翻转列表。

```python
nums.reverse()
```

- 修改原列表
- 返回值：`None`
- 时间复杂度：**O(n)**

示例：

```python
nums = [1, 2, 3]

nums.reverse()

print(nums)
# [3, 2, 1]
```

---

# 拼接列表

## +

创建一个新的列表。

```python
c = a + b
```

假设：

- `a` 长度为 `n`
- `b` 长度为 `k`

则：

- 不修改原列表
- 返回值：新的列表
- 时间复杂度：**O(n+k)**
- 空间复杂度：**O(n+k)**

示例：

```python
a = [1, 2]
b = [3, 4]

c = a + b

print(c)
# [1, 2, 3, 4]
```

> ⚠️ 注意  
> `+` 会创建新的列表，因此需要复制两个列表中的所有元素。

---

## +=

将右侧列表元素添加到左侧列表。

```python
a += b
```

- 通常修改原列表
- 无返回值
- 时间复杂度：**O(k)**

示例：

```python
a = [1, 2]
b = [3, 4]

a += b

print(a)
# [1, 2, 3, 4]
```

---

# 常用操作复杂度汇总

| 操作 | 含义 | 是否修改原列表 | 时间复杂度 |
|---|---|---|---|
| `nums[i]` | 按下标访问 | 否 | O(1) |
| `nums[i]=x` | 修改指定位置 | 是 | O(1) |
| `append(x)` | 末尾添加一个元素 | 是 | 摊还 O(1) |
| `extend(other)` | 添加多个元素 | 是 | O(k) |
| `insert(i,x)` | 指定位置插入 | 是 | O(n) |
| `pop()` | 删除末尾元素 | 是 | O(1) |
| `pop(i)` | 删除指定位置元素 | 是 | O(n) |
| `remove(x)` | 按值删除 | 是 | O(n) |
| `clear()` | 清空列表 | 是 | O(n) |
| `index(x)` | 查找元素位置 | 否 | O(n) |
| `count(x)` | 统计出现次数 | 否 | O(n) |
| `x in nums` | 判断是否存在 | 否 | O(n) |
| `sort()` | 原地排序 | 是 | O(n log n) |
| `sorted()` | 返回排序结果 | 否 | O(n log n) |
| `reverse()` | 原地翻转 | 是 | O(n) |
| `a+b` | 创建新列表拼接 | 否 | O(n+k) |
| `a+=b` | 原地扩展 | 是 | O(k) |
## List 与 [[字典(dictionary)|Dict]] 的简单对比

| 特点    | List               | Dict                   |
| ----- | ------------------ | ---------------------- |
| 访问方式  | 下标                 | 键                      |
| 查找复杂度 | `x in nums` 为 O(n) | `key in data` 平均为 O(1) |
| 适合场景  | 有序序列、按位置访问         | 映射、计数、快速查找             |
相关笔记：[[字典(dictionary)]]