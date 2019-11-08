---
title: "python_5_try_except"
excerpt: try, except, finall, raise, 예외처리
header:
 overlay_image: /assets/images/overlayimage.jpg
categories:
  - python
tags:
  - python
use_math: true
toc: true
toc_label: "페이지 주요 목차"
toc_sticky: true
---
## try except
```python
ls = [1, 2, 3]
try:
    print(ls[3])
except:
    print("error")
print("done!")
```

```python
try:
    5/0
except IndexError as e:
    print(e)
print("done!")
```

```python

```
## finall
```python
is_error = False

try:
    1/0
except Exception as e:
    print(e)
    is_error = True
finally:
    print("is error", is_error)

=> division by zero
   is error True
```
```python

```
```python

```
## raise
```python
try:
    5/0
except Exception as e:
    print(e)
    raise(e)
print("done!")
```
