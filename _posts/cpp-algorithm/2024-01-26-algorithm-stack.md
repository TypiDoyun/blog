---
title: "[C++ / Algorithm] 스택 #6"
date: 2024-01-26 23:19:00 +/-TTTT
categories: [algorithm, cpp]
tags: [algorithm, cpp]   # TAG names should always be lowercase
---

## 1. 스택이란?

스택은 데이터를 맨 아래에서 차곡차곡 쌓는 형태의 자료구조입니다.<br>
맨 처음에 넣은 데이터는 마지막엔 맨 아래에 깔려있게 되므로<br>
제일 먼저 들어온 데이터가 제일 늦게 나간다는 **선입후출**의 특징이 있습니다. 

----

## 3. C++에서의 스택

C++에서는 보통 아래와 같이 스택을 사용합니다.

```cpp
#include <iostream>
#include <stack>

using namespace std;

int main() {
    stack<int> myStack;

    myStack.push(1);
    myStack.push(2);
    myStack.push(3);

    cout << myStack.top() << " ";
    myStack.pop();
    cout << myStack.top() << " ";
    myStack.pop();
    cout << myStack.top() << " ";
    myStack.pop();

    return 0;
}
```
{: file="main.cpp" }
```
3 2 1 
```
{: file="output.txt" }

스택은 가장 먼저 들어온 데이터가 가장 마지막에 사용되며,<br>
**`push`** 메소드로 값을 넣거나 **`top`** 메소드로 가장 최근에 들어간 데이터를 확인할 수 있습니다.
**`pop`** 메소드는 가장 최근에 들어간 데이터 하나를 지우는 메소드입니다.
