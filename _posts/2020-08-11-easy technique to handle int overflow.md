---
title: "[Algorithm]정수 범위를 넘는 산술 연산의 간단한 처리법"
layout: post
date: 2020-08-11
image: /assets/images/markdown.jpg
headerImage: false
tag:

- Algorithm
category: blog
author: lucas-jang
description: What is 1LL?
---


![ViewCount](https://views.whatilearened.today/views/github/<user>/<repo>.svg)

[1,2,3 더하기 3]( https://www.acmicpc.net/problem/15988) 문제 참조

---

정수 리터럴(int)끼리 산술연산을 수행할 때 그 범위를 넘어서는 값이 발생하는 경우가 있다.

이전까지는

```c++
int dp[1000001];
dp[i] = (int)(((long long)dp[i - 1] + (long long)dp[i - 2] + (long long)dp[i - 3]) % (long long)1000000009);
```

위와 같이 일일이 int값들에 (long long)과 같이 캐스팅을 하였지만 더 간단한 방법이 있어 기록해둔다.

```c++
dp[i] = (1LL*dp[i - 1] + dp[i - 2] + dp[i - 3]) % 1000000009;
```



## 1LL 이 무엇인가?

'LL'은 리터럴 접미사(suffix)이다. [^1]

| **접미사** |     **자료형**     |
| :--------: | :----------------: |
|    생략    |        int         |
|    l, L    |        long        |
|    u, U    |    unsigned int    |
|   ul, UL   |   unsigned long    |
|   ll, LL   |     long long      |
|  ull, ULL  | unsigned long long |



따라서 1LL은 long long 타입의 수 '1'이다. 



## 1LL을 곱하는 이유는?

C 언어에서는 자료형을 섞어서 쓰면 컴파일러에서 암시적 형 변환(implicit type conversion)을 하게 되는데 자료형의 크기가 큰 쪽, 표현 범위가 넓은 쪽으로 형확장이 된다.[^2]

따라서 이후에 int타입의 수를 곱해도 long long 으로 확장되어 있으므로 따로 캐스팅을 해줄 필요가 없다.



## long long 타입을 int 배열에 저장을 하게 되는데?

이 문제의 계산식에서 % 1000000009 의 연산이 계산된 최종값이 int 범위를 넘어가지 않도록 보장해주므로 따로 (int) 캐스팅을 해주지 않아도 원하는 값을 배열에 정수형으로 저장할 수 있다.

---

[^1]:  [정수 리터럴 접미사 사용하기](https://dojang.io/mod/page/view.php?id=71)
[^2]: [자료형의 확장과 축소 알아보기](https://dojang.io/mod/page/view.php?id=112)

---
