---
layout: mypost
title: Python Linar Structure Interview Questions
categories: [Python]
---


### 1. Second Max of Array

1. select the first two elements as *best* and *second best*
2. if new > best: update best
3. if new > second_best: update second best

### 2. Reverse Integers

`int(str(num)[::-1])`

### 3. Fizz Buzz

`range(start : end : step)`

### 4. Array List

**Useful Operations**:

* `del list[index]`
* `list.index(value`) *return the index of the first encountered val*
* `[i for i in range(n)]`

### 5. Remove Duplicate Numbers in Arrary

1. if list is empty: return 0
2. sort list
3. set count = 1
4. iterate list and compare elements two by two
5. if first != second: set list[count] = second and count++

In this way, when we encounter two elements with the same value, the second one will always be replace by the next.

For example, [1, 3, 3, 2, 5] -> [1, 3, 2, 2, 5] -> [1, 3, 2, 5, 5]

### 6. Remove Element

**Useful Operations**:

* `range(len(list) - 1, -1, -1)` *from end to start*
* `list[i], list[j] = list[j], list[i]` *swap*

### 7. Valid Palindrome

1. set start and end
2. while start < end
3. igonre irrelavent characters and compare characters
4. dont forget to increment!

### 8. Reverse Words in a String

`' '.join(reversed(str.strip().split()))`
