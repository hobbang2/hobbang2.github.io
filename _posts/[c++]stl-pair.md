---
layout: post
title:  "[C++]STL Pair"
date:   2019-05-24 14:26:12
published: true
categories: [C++]
comments: true
image:
  feature: https://www.stickyminds.com/sites/default/files/article/2018/RubberDucks.jpg
---

## **이번 포스팅에서 알아볼 내용**
### [C++ STL pair]
<!--more-->
C++로 코드를 작성할 때 STL을 이용하면 편리하다.

pair는 <utility> 라는 라이브러리에 있는 container이다.

두 개의 자료형을 함께 보관(?)할 수 있다.

pair <int,int> p

pair <int,float> p

pair <People,int> p 등등

PS를 하다가 pair의 pointer를 사용할 일이 생겼는데, 괜히 pair <int,int> 로 선언하니까 헷갈리더라 

### pair <int,int> & p
``` cpp
pair <int, int> tmp = { 987654321,123456789 };
	pair <int, int> & p = tmp;
	cout << p->first << " " << p->second << endl;
```
출력 값은 무엇일까 ? 

987654321 123456789

``` cpp
p.first = 4, p.second = 5;
cout << tmp.first << " " << tmp.second << endl;
```
출력 값은 무엇일까 ? 

4 5

``` cpp
	pair <int, int> k = { 7,8 };
	p = k;
	cout << p->first << " " << p->second << endl;
	cout << tmp.first << " " << tmp.second << endl;
```
출력값은 무엇일까?

7 8  
7 8

당연하게도 tmp의 값이 변경된다. 

tmp의 별명인 p에 k를 대입해준 꼴이니

그런데 나는 tmp의 값을 그대로 두고 싶었다. 

그러면 pointer를 사용해야한다. 

```cpp
	pair <int, int> tmp = { 987654321,123456789 };
	pair <int, int> * p = &tmp;
	cout << p->first << " " << p->second << endl;
```
이하 코드 생략^_^ 

원하는 결과를 얻을 수 있다. 
