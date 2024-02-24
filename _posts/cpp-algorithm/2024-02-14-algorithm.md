---
title: "[C++ / Algorithm] 브루트 포스란? #18"
date: 2024-02-14 23:02:00 +/-TTTT
categories: [algorithm, cpp]
tags: [algorithm, cpp]   # TAG names should always be lowercase
---

## 1. 브루트포스란?

브루트포스 알고리즘은 **`brute(무식한)`**과 **`force(힘)`**의 합성어로 뜻 그대로 무식하게 모든 경우의 수를 다 확인하는 알고리즘이다.

브루트포스는 해가 존재할 것으로 예상되는 모든 영역을 전부 탐색하는 방법이므로 시간 복잡도가 높은 편에 속합니다.

## 2. 약수 구하기

브루트 포스 알고리즘을 이용해서 약수를 구할 수 있습니다.

```cpp
#include <iostream>

using namespace std;

void printDivisor(int);

int main() {
    printDivisor(50);

    return 0;
}

void printDivisor(int x) {
    for (int divisor = 1; divisor <= x; divisor++) {
        if (x % divisor == 0) cout << divisor << endl;
    }
}
```
{: file="main.cpp" }
```
1
2
4
5
10
20

```
{: file="output.txt" }