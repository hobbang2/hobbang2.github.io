---
layout: post
title:  "[kaggle]1. 캐글을 시작해보자"
date:   2019-05-13 22:26:12
published: true
categories: [kaggle]
comments: true
image:
  feature: ./post_image/kaggle.PNG
---

## **이번 포스팅에서 알아볼 내용**
### [[kaggle]캐글 시작하기]
<!--more-->
다른 사람이 한 Big Data 분석 결과도 볼 수 있고, 잘하면 상금까지 거머쥘 수 있는 kaggle...!

미루고 미루어 왔던 데이터 분석을 이제야 시도해보려고 한다. 

아래는 참고한 포스팅들 - 감사합니다(__) -

1. [Kaggle에 대해서 알아보자!!](https://bit.ly/2vY5cuN)

2. [Kaggle에서 얻을 수 있는건?](https://bit.ly/2Vo9oya)

여차저차해서 Kaggle에 가입까지 하고, 첫 kernel을 만들었다. 

두번째 글에서 인용하자면 `모방은 창조의 어머니` 동의한다 ^_^

무작정 시작하기 보다는, 잘하는 사람의 kernel을 필사하는 것부터 하기로 했다.

### 입문
[![quick and draw!](./post_image/quick_draw.JPG)](https://bit.ly/2JiHAtt)

### 커널 필사 
#### 1. [Getting Started: Viewing Quick, Draw! Doodles, etc](https://bit.ly/2vY8xKi)
![quick_draw_1_result](./post_image/quick_draw_1_result.JPG)

- 파이썬에서 data를 읽고, 분석할 준비
- raw drawing data를 simple 하게 바꾸어줌 ( ex. 8개의 점으로 연결된 직선을 2개의 점으로 연결된 직선으로 갼결화)
- 정해진 format에서 prediction을 포함한 submission을 만드는 방법

string 값으로 저장된 drawing data를 list로 바꾸어주기 위해 ast.literal_eval

오차 범위 내에서 직선을 간결하게 해주기 위해 [simplification](https://bit.ly/30fCtPY).cutil라이브러리 내의 simplify_coords

를 사용합니다. 

#### 2. [QuickDraw Baseline LSTM Reading and Submission](https://bit.ly/2Hl2apI)
drawing data를 간결하게 만들었다면, 이제 이 데이터를 사용할 차례.

이번 kernel에서는 이 데이터와 LSTM network를 이용한다.

해당 kernel의 model은 stroke data를 받아 1D convolution으로 preprocessing을 한뒤,

two stacked LSTMs 로 classification을 한다. 

kernel 작성자가 제시한 더 나은 결과를 위한 세가지 

- train data를 더 많이 쓰는 것
- 같은 주제라도 country 마다 다른 그림,방법을 사용하므로 county code 를 포함하는 것
- 더 복잡한 모델을 사용하는것

