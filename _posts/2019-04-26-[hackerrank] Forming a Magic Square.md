---
layout: post
title:  "[hackerrank] Sock Merchant"
date:   2019-04-26 14:26:19
categories: [PS]
comments: true
image:
  feature: https://cdn.pixabay.com/photo/2014/03/06/23/05/gaudi-281290_1280.jpg
---

## **이번 포스팅에서 알아볼 내용**
### [[Medium]Forming a Magic Sqauare](https://bit.ly/2sl9VVa)
<!--more-->
### [1. 문제 소개](#1.-문제-소개)

### [2. 알고리즘](#2.-알고리즘)

## **그럼 공부를 해볼까요?**

### 1. 문제 소개

#### 문제 설명
N x N 행렬이 주어집니다. 

이 정사각행렬의 가로, 세로, 대각선에 있는 숫자의 합이 각각 같도록 만들어주면 됩니다. 

예를 들어, 

5 3 4 

1 5 8        

6 4 2 

에서 1행 1열의 5를 8로, 2행 3열의 8을 9로, 3행 2열의 4를 7로 바꾸어주면 

8 3 4

1 5 9

6 7 2

가 되고, 가로, 세로, 대각선의 합이 모두 15로 동일하게 됩니다. 

이런 정사각행렬을 `magic square` 라고 부릅니다.

이렇게 주어진 정사각행렬에서 숫자를 바꾸어 'magic square'가 되도록 만들어주면 됩니다. 

그런데, 기왕이면 숫자의 변화 폭이 작으면 좋겠어요 ! 

위에서 magic square를 만들어 줄 때, 5->8, 8->9, 4->7 로 변하였으니 변화 폭(cost)은 7이 돼요.

magic suare는 여러 개가 있을텐데, 이중에서 변화 폭(cost)이 가장 작은 것을 찾아주면 됩니다.

#### Input data
3x3 정사각행렬이 주어집니다. 

한 줄에 숫자가 3개씩 총 3개가 나옵니다. 

예를 들면 요로케 

    4 9 2

    3 5 7

    8 1 5
    
#### Constraints
$s[i][j] \in [1,9]$

9개의 숫자로 만들 수 있는 3 x 3 행렬은 $9^{9} = 387420489$ 약 3억개로 21억 보다 한 참 작네요!_! 

### 2. 알고리즘

#### 알고리즘 설명
9개의 숫자를 조합해서 만들 수 있는 행렬이 약 3억개니까 모두 찾아줄거에요. 

그런데 숫자의 조합은 1차원이자나용, 그런데 행렬은 2차원 !

1차원으로 표현된 숫자의 조합을 행과 열로 나타내서 비교하려면 어떻게 하느냐 ~_~ 

`3*i+j` 로 나타냅니당.

왜냐하면, 0, 1, 2, 3, 4, 5, 6, 7, 8 을 3으로 나누었을 때의 몫이 행, 나머지가 열이 되기 때문이지요.

이렇게 바꾼 다음에는 가로, 세로, 대각선의 합이 같은지 비교해주면 됩니다. 

#### 코드 설명 [C/C++]
1) next_permutation

#### 코드 [C/C++]
```c++
def sockMerchant(n, ar):
    result = 0
    dic_sock = defaultdict(lambda:0)
    for idx in ar:
        dic_sock[idx]+=1
    for idx in dic_sock.keys():
        result+= math.floor(dic_sock[idx]/2)
    return result
```