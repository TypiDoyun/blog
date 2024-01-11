---
title: "[C++] 스마트 포인터란? #14"
date: 2024-01-11 23:48:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop]     # TAG names should always be lowercase
---

## 1. 스마트 포인터의 필요성
C++에서 `new` 연산자를 이용해서 할당받은 메모리는 `delete` 연산자로 해제하지 않는 경우 메모리 누수가 발생합니다.<br>
이러한 상황을 막기 위해 C++에서는 메모리를 자동으로 해제해주는 스마트 포인터를 지원하고 있습니다.

## 2. 스마트 포인터 사용법
스마트 포인터는 대표적으로 `unique_ptr`이 있습니다.<br>
아래 코드는 스마트 포인터를 생성하는 코드입니다.

```cpp
#include <memory>

using namespace std;

int main() {
    unique_ptr<int> number(new int(5));

    return 0;
}
```
{: file="main.cpp" }
위 코드는 정수형 변수를 스마트 포인터로 동적 할당한 코드입니다.<br>
스마트 포인터를 사용하였기 때문에 `delete` 연산자로 `number`가 점유하는 메모리를 해제하지 않아도 됩니다.

## 3. make_unqiue 사용하기
C++14 부터는 `make_unique`라는 함수를 이용해 더 안전하게 스마트 포인터를 생성할 수 있습니다.<br>
`make_unique`는 전달받은 매개변수를 바탕으로 해당 타입의 객체를 생성합니다.

```cpp
#include <iostream>
#include <memory>

using namespace std;

class MyObject {
public:
    int myProperty;

    MyObject(int myProperty) {
        this->myProperty = myProperty;
        cout << "생성자가 호출되었습니다." << endl;
    }

    ~MyObject() {
        cout << "소멸자가 호출되었습니다." << endl;
    }
};

int main() {
    unique_ptr<MyObject> obj = make_unique<MyObject>(5);

    cout << obj->myProperty << endl;

    return 0;
}
```
{: file="main.cpp" }
```
생성자가 호출되었습니다.
5
소멸자가 호출되었습니다.
```
{: file="output.txt" }

위 코드에서 `unique_ptr`이 객체의 메모리를 자동으로 해제해주는 것을 확인할 수 있습니다.