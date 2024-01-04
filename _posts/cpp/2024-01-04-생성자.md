---
title: "[C++] 생성자와 소멸자 #7"
date: 2024-01-04 22:06:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop] # TAG names should always be lowercase
---

## 1. 생성자
생성자는 ***클래스가 객체를 생성할 때 실행되는 함수*** 입니다.<br>
생성자는 매개변수를 받아 속성에 값을 할당하고 객체를 생성하는 등 말 그대로의 생성의 역할을 담당합니다.

```cpp
class Human {
public:
    int age;
    int height;

    Human(int age, int height) {
        this->age = age;
        this->height = height;
    }
}
```
{: file="main.cpp" }
위 코드는 생성자의 매개변수로 받은 `age`와 `height`를 객체 속성에 값으로 할당하는 코드입니다.<br>

## 1-1. 기본 생성자
클래스는 생성자를 정의하지 않고 선언하는 경우 `기본 생성자`가 생성됩니다.<br>
`기본 생성자`는 매개변수 없이 존재하는 생성자로 생성된 객체에 속성들은 `0`또는 `NULL`로 할당됩니다.

```cpp
class Human {
public:
    int age;
    int height;
}

int main() {
    Human human();
}
```
{: file="main.cpp" }
`main`함수에서 Human을 생성할 때 생성자로 인자를 전달해주지 않는 모습을 볼 수 있습니다.

----

## 1-2. 복사 생성자
복사 생성자는 그 클래스로 생성된 다른 객체의 참조값을 매개변수로 받아 새로운 객체를 생성하는 생성자입니다.

```cpp
class Human {
public:
    int age;
    int height;

    Human(const Human& other) {
        age = other.age;
        height = other.height;
    }
}
```
{: file="main.cpp" }

복사 생성자를 이용하면 해당 객체의 속성값은 동일하게 가지고 있지만,<br>
서로 다른 메모리를 사용하고 있는 객체를 생성할 수 있습니다.<br>
따라서 복사 생성자를 이용하면 객체를 복사할 수 있습니다.

## 2. 소멸자
소멸자는 ***객체의 수명이 끝났을 때 실행되는 함수*** 입니다.<br>
객체가 사라질 때 직접 메모리를 해제해 줘야하는 속성을 관리할 때 유용합니다.

```cpp
class Human {
public:
    int age;
    int height;
    int* pointer = new int;

    ~Human() {
        delete pointer;
    }
}
```
위와 같이 소멸자는 `~`기호를 앞에 붙여 함수처럼 정의합니다.