---
title: "[C++] 인라인 함수란? #18"
date: 2024-01-15 23:30:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop]     # TAG names should always be lowercase
---

## 1. 인라인 함수의 필요성
C++에서 함수를 호출하는 과정은 복잡하기 때문에 시간이 오래걸립니다.<br>
하지만, 인라인 함수를 사용한다면 함수의 호출 시간을 단축시킬 수 있다는 장점이 있습니다.

----

## 2. 인라인 함수의 선언
인라인 함수는 아래 코드와 같이 선언합니다.

```cpp
#include <iostream>

using namespace std;

inline int multiply(int x, int y) { return x * y; }

int main() {
    int x = 30;
    int y = 2;

    cout << multiply(x, y) << endl;

    return 0;
}
```
{: file="main.cpp" }
```
60

```
{: file="output.txt" }

인라인 함수는 보통 리턴 값이 바로 있거나 아주 작은 코드를 가지고 있는 함수에 사용됩니다.

----

## 3. 인라인 함수의 장단점

### 3-1. 장점
* 함수의 호출 시간을 줄여 더 빠르게 코드를 실행할 수 있습니다.

----

### 3-2. 단점
* 함수의 코드를 실행된 위치에 삽입하는 방식으로 동작하기 때문에 함수를 사용하면서 얻는 이점을 얻을 수 없습니다.