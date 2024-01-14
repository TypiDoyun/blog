---
title: "[C++] 함수 포인터란? #16"
date: 2024-01-13 22:00:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop]     # TAG names should always be lowercase
---

## 1. 함수 포인터란?
함수 또한 메모리 어딘가에 함수가 저장되고 있습니다.<br>
따라서 그 함수의 위치를 가르키는 것이 ***함수 포인터*** 입니다.

## 2. 함수의 주소 확인하기
함수의 주소를 확인하는 방법은 일반 변수의 주소를 확인하는 것과 비슷합니다.

```cpp
#include <stdio.h>

void sayHello() {
    printf("Hello\n");
}

int main() {
    printf("pointer: %p\n", sayHello);

    return 0;
}
```
{: file="main.cpp" }
```
pointer: 0x401136

```
{: file="output.txt" }

## 3. 함수 포인터 선언하기
함수 포인터를 나타내는 자료형은 아래와 같이 씁니다.

```cpp
#include <stdio.h>

void sayHello() {
    printf("Hello\n");
}

int main() {
    void (*func)();

    func = sayHello;

    func();

    return 0;
}
```
{: file="main.cpp" }
```
Hello

```
{: file="output.txt" }

함수 포인터를 사용할 때는 함수의 반환값의 자료형과 매개변수 등이 일치해야 한다는 조건이 있습니다.
또한 `sayHello`의 메모리 주소를 가르키는 `func`를 실행한 결과가 `sayHello`의 실행 결과와 같습니다.

### 3-1. 매개변수와 반환값이 있는 함수의 경우
```cpp
#include <stdio.h>

int sumAndPrint(int a, int b) {
    printf("%d + %d = %d\n", a, b, a + b);

    return a + b;
}

int main() {
    int (*func)(int, int);

    func = sumAndPrint;

    int result = func(5, 10);

    printf("result: %d\n", result);

    return 0;
}
```
{: file="main.cpp" }
```
5 + 10 = 15
result: 15

```
{: file="output.txt" }

위 코드와 같이 작성하면 됩니다.