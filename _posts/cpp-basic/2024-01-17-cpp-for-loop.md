---
title: "[C++] 간단하게 배열 반복하기 #20"
date: 2024-01-17 22:45:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop]     # TAG names should always be lowercase
---

## 1. 기존의 배열 반복문
C언어에서는 배열을 반복하기 위해선 아래와 같이 반복할 인덱스를 선언하는 방법으로 해야 했습니다.

```cpp
#include <iostream>
#include <array>

using namespace std;

int main() {
    array<int, 10> arr = { 5, 12, 45, 2, 1, 6, 7, 2, 8, 9 };

    for (int i = 0; i < 10; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```
{: file="main.cpp" }
```
5 12 45 2 1 6 7 2 8 9 
```
{: file="output.txt" }

## 2. 범위 기반 for문
C++에서는 파이썬과 비슷하게 배열을 반복할 수 있습니다.
아래 코드는 `array`를 범위 기반 for문으로 반복하는 코드입니다.

```cpp
#include <iostream>
#include <array>

using namespace std;

int main() {
    array<int, 10> arr = { 5, 12, 45, 2, 1, 6, 7, 2, 8, 9 };

    for (int item : arr) {
        cout << item << " ";
    }

    return 0;
}
```
{: file="main.cpp" }
```
5 12 45 2 1 6 7 2 8 9 
```
{: file="output.txt" }

## 3. 범위 기반 for문의 장단점

### 3-1. 장점
* 인덱스 변수의 선언 필요 없이 배열의 길이만큼만 반복해줍니다.

### 3-2. 단점
* 인덱스 변수를 선언하지 않아 인덱스를 사용하는 경우에는 적절하지 않습니다.