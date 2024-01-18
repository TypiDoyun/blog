---
title: "[C++] 디폴트 인수란? #21"
date: 2024-01-18 23:24:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop]     # TAG names should always be lowercase
---

## 1. 디폴트 인수의 필요성
디폴트 인수는 함수의 매개변수로 인자가 전달되지 않았을 경우 기본적으로 할당되는 값입니다.<br>
디폴트 인수를 사용하면 특정 상황에서 코드를 조금 간결하게 작성할 수 있습니다.

## 2. 디폴트 인수 사용법
디폴트 인수는 아래와 같이 설정하고 사용합니다.<br>

```cpp
#include <iostream>

using namespace std;

int power(int x, int y = 2) {
    int result = 1;

    for (int i = 0; i < y; i++) {
        result *= x;
    }

    return result;
}

int main() {
    cout << power(2, 0) << endl;
    cout << power(2, 1) << endl;
    cout << power(2, 2) << endl;
    cout << power(2) << endl;

    return 0;
}
```
{: file="main.cpp" }
```
1
2
4
4

```
{: file="main.cpp" }

`power` 함수의 `y` 인자를 전달하는 경우엔 그 값으로 실행되지만,<br>
값을 전달하지 않으면 함수 선언부에서 설정한 디폴트 인수로 할당됩니다.

## 3. 디폴트 인수 사용시 주의점

디폴트 인수를 사용할 때는 아래 내용을 주의해야합니다.

* 디폴트 인수는 함수의 원형에만 지정할 수 있습니다.
* 디폴트 인수는 매개변수의 오른쪽부터 설정해야 합니다.