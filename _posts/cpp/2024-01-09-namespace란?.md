---
title: "[C++] namespace란? #12"
date: 2024-01-09 19:50:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop] # TAG names should always be lowercase
---

## 1. namespace를 쓰는 이유
C++에는 다양한 라이브러리가 있습니다.<br>
이 다양한 라이브러리에서 사용하는 함수나 변수는 이름이 겹쳐 충돌하는 상황이 발생할 수 있습니다.<br>
C++를 이를 해결하기 위해 `namespace`라는 개념을 사용하고 있습니다.

## 2. namespace의 정의
`namespace`를 정의하기 위해선 `namespace`라는 키워드를 사용해야 합니다.<br>
`namespace`는 코드 전역 위치 또는 다른 `namespace` 내부에서도 정의될 수 있습니다.

```cpp
namespace typidoyun {
    int age;
    int height;
}
```
{: file="namespace.h" }

## 3. namespace의 사용
`namespace`를 사용하는 방법은 `namespace::사용할것`입니다.<br>
대표적인 예시로는 `std::cout`이 있습니다.

```cpp
#include "namespace.h"

int main() {
    typidoyun::age = 19;
    typidoyun::height = 180;

    return 0;
}
```
{: file="main.cpp" }

## 4. namespace 간편하게 사용하기
출력할 때 계속 `std::`라는 키워드를 사용하면 코드가 귀찮아지기 때문에<br>
`using`이라는 지시자를 사용할 것입니다.

```cpp
#include <iostream>

using namespace std;

int main() {
    cout << "간편하다.";

    return 0;
}
```
{: file="main.cpp" }
```
간편하다.
```
{: file="output.txt" }

위 코드에서 `using namespace std`를 사용해서 `namespace`를 단축하고 있습니다.<br>