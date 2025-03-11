---
title: "[Linear Algebra] 선형변환에 대한 이해 #2"
date: 2024-10-31 16:06:00 +/-TTTT
categories: [math, linear-algebra]
tags: [math, linear-algebra, matrix, vector, linear-transform]   # TAG names should always be lowercase
---

{% include math.html %}

## 1. 선형변환이란?
선형변환은 선형대수학에서 가장 중요한 개념중 하나입니다.<br>
선형변환은 **<u>벡터 공간에서 다른 벡터 공간으로의 변환</u>**을 의미합니다.<br>
이러한 변환은 **<u>선형성</u>**을 만족해야 합니다.<br>

## 2. 선형변환의 정의
선형변환은 다음과 같은 조건을 만족해야 합니다.<br>
1. **<u>덧셈에 대한 선형성</u>**<br>
    $_
    T(\vec{u} + \vec{v}) = T(\vec{u}) + T(\vec{v})
    _$<br>
2. **<u>스칼라배에 대한 선형성</u>**<br>
    $_
    T(k\vec{u}) = kT(\vec{u})
    _$<br>

위와 같은 조건을 만족하는 변환을 **<u>선형변환</u>**이라고 합니다.<br>