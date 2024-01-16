---
title: "[C++] 람다 함수란? #19"
date: 2024-01-16 23:31:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop]     # TAG names should always be lowercase
---

## 1. 람다 함수의 필요성
C++에서는 함수를 인자로 전달하는 경우가 있습니다.<br>
예를 들어, `algorithm` 헤더 파일에 있는 `sort`라는 함수의 경우<br>
인자로 이터레이터 2개와 함수를 받습니다.

```cpp
#include <iostream>
#include <algorithm>

using namespace std;

int cmp(int a, int b) {
    return a < b;
}

int main() {
    vector<int> arr = { 10, 2, 4, 1, 6, 0, 20 };

    sort(arr.begin(), arr.end(), cmp);

    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```
{: file="main.cpp" }
```
0 1 2 4 6 10 20 
```
{: file="output.txt" }

위 코드와 같이 선언된 함수 `cmp`를 함수의 인자로 전달하고 있습니다.<br>
위 코드처럼 인자로 전달되기 위해서 선언되는 함수를 간단하게 사용하기 위해 람다함수가 사용됩니다.

## 2. 람다 함수 사용법
람다 함수는 아래 코드와 같이 사용할 수. 있습니다.

```cpp
#include <iostream>
#include <algorithm>

using namespace std;

int main() {
    vector<int> arr = { 10, 2, 4, 1, 6, 0, 20 };

    sort(arr.begin(), arr.end(), [](int a, int b) { return a < b; });

    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```
{: file="main.cpp" }
```
0 1 2 4 6 10 20 
```
{: file="output.txt" }

## 3. 람다 함수의 구조

람다 함수는 크게 3가지로 구분됩니다.

1. 캡쳐 영역 - []
2. 매개변수 영역 - ()
3. 코드블록 영역 - {}

매개변수와 코드블록 영역은 예전에 배운 일반 함수와 동일하지만,<br>
캡쳐 영역이라는 것이 새로 생겼습니다.

캡쳐 영역은 함수 내부에서 함수 외부에 있는 변수를 어떻게 사용할 것인지 명시해주는 역할입니다.

대표적으로 참조를 하는 `&` 연산자와 값을 복사하는 `=` 연산자가 있습니다.

### 3-1. & 연산자
`&` 연산자는 외부에 있는 모든 변수를 참조하여 함수 내부에서 사용하겠다는 의미입니다.<br>
따라서 복사가 발생하지 않고, 외부에서 선언된 정수형 변수 `a`의 값을 람다 함수 안에서 수정한다면<br>
외부에 있는 변수 `a`도 값이 수정됩니다.

### 3-2. = 연산자
`=` 연산자는 외부에 있는 모든 변수를 복사하여 함수 내부에서 사용하겠다는 의미입니다.

아래는 각각의 연산자를 사용한 코드입니다.

```cpp
#include <iostream>
#include <algorithm>

using namespace std;

int main() {
    int a = 10;

    [a]() {
        cout << "a: " << a << endl;
    }();

    [&]() {
        a = 3;
    }();

    cout << "a: " << a << endl;

    return 0;
}
```
{: file="main.cpp" }
```
a: 10
a: 3

```
{: file="output.txt" }

## 4. 특정 변수만 복사하거나 참조하기
람다 함수는 특정 변수만 복사하거나 참조할 수 있습니다.

아래 코드는 `a`라는 변수를 복사하고 `b`라는 변수를 참조하는 코드입니다.

```cpp
#include <iostream>
#include <algorithm>

using namespace std;

int main() {
    int a = 10;
    int b = 20;

    [a, &b]() {
        cout << "a: " << a << endl;
        cout << "b: " << b << endl;
    }();

    return 0;
}
```
{: file="main.cpp" }
```
a: 10
b: 20

```
{: file="output.txt" }