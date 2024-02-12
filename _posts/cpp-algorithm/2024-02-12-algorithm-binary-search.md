---
title: "[C++ / Algorithm] 이진 탐색이란? #17"
date: 2024-02-12 16:23:00 +/-TTTT
categories: [algorithm, cpp]
tags: [algorithm, cpp]   # TAG names should always be lowercase
---

## 1. 이진 탐색이란?

이진 탐색은 정렬된 데이터들 중 특정한 데이터를 빠르게 찾아낼 수 있는 알고리즘입니다.<br>
이진 탐색을 하기 위해선 무조건 데이터가 정렬되어 있어야 한다는 조건이 있습니다.

----

## 2. 이진 탐색의 원리

오름차순으로 정렬된 데이터는 특정 데이터를 기준으로 그 데이터보다 값이 큰 데이터는 오른쪽에 있고,<br>
작은 데이터는 왼쪽에 있을 것입니다. 이진 탐색은 이러한 점을 이용해서 탐색을 진행합니다.

길이 10짜리의 정렬된 데이터들 중 이진 탐색을 이용해서 12를 찾아보겠습니다.

----

### 2-1. 중간값 설정하기

![image](/assets/cpp-algorithm/17/1.png)

배열의 길이를 기준으로 절반 정도에 중간값을 잡아줍니다.

----

### 2-2. 중간값과 목표값을 비교하기

![image](/assets/cpp-algorithm/17/2.png)

목표값이 중간값보다 크다면 중간값 기준으로 오른쪽의 배열을,<br>
목표값이 중간값보다 작다면 중간값 기준으로 왼쪽의 배열을 선택해줍니다.

만약 여기서 목표값과 중간값이 같다면 탐색을 완료하게 됩니다.

----

### 2-3. 값을 찾을 때까지 위 과정을 반복하기

![image](/assets/cpp-algorithm/17/3.png)

다시 목표값과 비교하기 위한 중간값을 지정합니다.

![image](/assets/cpp-algorithm/17/4.png)

![image](/assets/cpp-algorithm/17/5.png)

![image](/assets/cpp-algorithm/17/6.png)

![image](/assets/cpp-algorithm/17/7.png)