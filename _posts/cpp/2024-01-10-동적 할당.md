---
title: "[C++] 동적 할당 #13"
date: 2024-01-10 23:38:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop] # TAG names should always be lowercase
---

## 1. 동적 할당이란?
프로그램이 실행되는 도중을 ***런 타임*** 이라고 합니다.<br>
프로그램의 메모리 할당은 일반적인 경우 ***컴파일 타임*** 에 결정되지만,<br>
동적 할당을 이용한다면 프로그램이 실행되는 도중인 ***런 타임*** 에 메모리를 할당받을 수 있게 됩니다.

----

## 2. C++의 동적 할당
C++에서는 `new` 연산자로 메모리 동적 할당을 `delete` 연산자로 메모리 해제를 할 수 있습니다.

## 2-1. new 연산자

C++에서 `new` 연산자는 아래와 같이 사용합니다.
```cpp
int main() {
    int* numberPointer = new int;

    return 0;
}
```
{: file="main.cpp" }

위 코드는 `int` 자료형의 메모리를 할당하고<br>
그 메모리의 위치를 `numberPointer`라는 포인터 변수에 저장하는 코드입니다.<br>
위와 같이 메모리 동적 할당으로 받은 값은 메모리의 이름이 없으므로, 포인터로만 접근할 수 있습니다.

## 2-2. delete 연산자
메모리를 동적 할당한 후 사용하지 않는 메모리는 ***메모리 누수*** 가 발생하지 않게 해제해줘야 합니다.

```cpp
int main() {
    int* numberPointer = new int;

    delete numberPointer;

    return 0;
}
```
{: file="main.cpp" }

위 코드는 동적 할당된 메모리 `numberPointer`를 해제해주는 코드입니다.<br>

 > delete 연산자는 new 연산자로 할당된 메모리를 해제할 때에만 사용해야 합니다.
{: .prompt-warning }
 > 또한 동적 할당된 메모리를 해제하지 않으면 메모리가 한 공간을 계속 점유하는 ***메모리 누수*** 가 발생할 수 있습니다.
{: .prompt-warning }