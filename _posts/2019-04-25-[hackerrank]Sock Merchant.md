---
layout: post
title:  "[hackerrank] Sock Merchant"
published: false
date:   2019-04-25 21:31:19
categories: [PS]
comments: true
image:
  feature: https://image.shutterstock.com/z/stock-vector-set-of-socks-in-a-different-pattern-flat-vector-illustration-isolated-on-white-background-481743646.jpg
---

## **이번 포스팅에서 알아볼 내용**
### [easy-Sock Merchant](www.hackerrank.com/challenges/sock-merchant/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup
)
<!--more-->
### [1. 문제 설명](###문제-설명)

## **그럼 공부를 해볼까요?**

### 1. 문제 소개

#### 문제 설명
John이라는 양말장수가 양말 보따리를 들고 왔습니다. 이 중에서 짝이 맞는 것(색이 똑같은거)만 팔 수 있어요.
John은 몇 쌍의 양말을 팔 수 있을까요? 

#### Input data
n: the number of socks in the pile
ar: the colors of each sock
첫 줄에 정수 n 이 주어지고, 다음 줄에 n개의 정수(양말의 색깔을 표현)가 배열 ar에 담아집니다.

#### Constraints
$ 1<= n <= 100 $
$ 1<= ar[i] <= 100 where 0 <= i <n $
수의 범위를 걱정할 일은 없겠네요 ㅎㅎ

### 2. 알고리즘

#### 알고리즘 설명
ar에는 양말의 색깔을 표현하는 숫자들이 n 개 들어있습니다. 
ar은 리스트이므로, ar 안의 원소를 돌면서 각각의 개수를 세어줍니다.
그런 다음, 세어진 개수 / 2 해서 내림을 해주면 각 색깔 마다 양말 쌍의 개수가 구해집니다. 
왜 내림을 하냐면, 빨간색 양말이 3개 있을 때 나누기 2를 하면 1.5가 되는데 0.5개의 양말로는 한 쪽 발 밖에 신지 못하기 때문이에요.

#### 코드 설명 [Python3]
from collections import defaultdict
1) dic_sock = defaultdict(lambda:0)
- 값이 0으로 채워진 default dictionary를 생성합니다. 
- defaultdict(object) 등 임의의 object로 값을 채울 수도 있어요.
```python
from collections import defaultdict
dic_sock = defaultdict(lambda:0)
print("dic_sock["a"]") 
# 0이 출력됩니다.
```
KeyError가 발생하지 않고 미리 채워둔 값이 출력됩니다. 

2) dict.keys()
```python
first_name = {'kim': 3, 'heo': 2, 'song': '1'}
print(first_name.keys())
# dict_keys(['kim', 'heo', 'song'])
```
dictionary의 key가 출력됩니다.

3) dict.items()
```python
print(first_name.items())
# dict_items([('kim', 3), ('heo', 2), ('song', 1)])
```
dictionary의 key,value 쌍이 출력됩니다. 

#### 코드 [Python3]
```python
def sockMerchant(n, ar):
    result = 0
    dic_sock = defaultdict(lambda:0)
    for idx in ar:
        dic_sock[idx]+=1
    for idx in dic_sock.keys():
        result+= math.floor(dic_sock[idx]/2)
    return result
```
