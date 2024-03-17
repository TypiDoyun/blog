---
title: "[C++ / Design Pattern] 싱글톤 패턴 #2"
date: 2024-03-17 22:12:00 +/-TTTT
categories: [design-pattern, cpp]
tags: [design-pattern, cpp]   # TAG names should always be lowercase
---

## 1. 싱글톤 패턴이란?

싱글톤 패턴은 어떠한 클래스의 인스턴스가 오직 1개만 생성되는 패턴을 의미합니다.<br>
싱글톤 패턴을 다양한 방법으로 구현될 수 있지만,<br>
이번 예시에서는 인스턴스를 얻어올 때 전에 생성된 인스턴스가 있는지 검사하는 방식으로 구현하겠습니다.

## 2. 싱글톤 구현

```cpp
#include <stdlib.h>
#include <iostream>

using namespace std;

class Singleton {
public:
    int value = 0;

    static Singleton* getInstance() {
        if (instance == nullptr) {
            instance = new Singleton();
            atexit([]() {
                delete instance;
            });
        }
        return instance;
    }

private:
    Singleton() {};
    Singleton(const Singleton& other) {};
    ~Singleton() {};

    static Singleton* instance;
};

Singleton* Singleton::instance = nullptr;

int main() {
    Singleton* singleton1 = Singleton::getInstance();
    Singleton* singleton2 = Singleton::getInstance();

    cout << singleton1->value << endl;

    singleton2->value = 5;

    cout << singleton1->value << endl;
}
```
{: file="main.cpp" }
```
0
5

```
{: file="output.txt" }

위에서 사용된 함수 atexit은 프로그램이 종료되기 직전에 호출될 함수를 등록해주는 함수입니다.<br>
따라서 new 연산자로 생성된 객체로 인한 메모리 누수를 막을 수 있습니다.

또한 실행 결과로 알 수 있듯이 **`singleton2`** 객체의 **`value`** 프로퍼티를 5로 할당하고<br>
**`singleton1`** 객체의 **`value`** 프로퍼티를 출력한 결과 5가 출력된 것을 확인할 수 있습니다.<br>
이는 싱글턴 패턴의 특징 때문으로 **`Singleton`** 클래스의 인스턴스는 실질적으로 1개만 생성되기 때문에<br>
**`singleton1`**와 **`singleton2`**가 동일한 객체를 가르키는 포인터라는 것을 알 수 있습니다.