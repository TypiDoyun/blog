---
title: "[C++] 포인터란? #5"
date: 2024-01-02 17:43:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop]     # TAG names should always be lowercase
---

## 1. 포인터의 개념
포인터란 변수의 위치를 기억하는 변수라고 볼 수 있습니다.<br>
포인터는 메모리의 효율적인 관리를 위해 등장했으며, 메모리의 주소를 직접적으로 기억하고 있습니다.

----

## 2. 포인터 사용해보기
포인터에서 대표적으로 사용하는 기호는 `*`와 `&`가 있습니다.<br>

### 2-1. & 기호
***`&`기호는 그 값의 메모리 주소를 반환시켜주는 기호*** 입니다.<br>

```cpp
int main() {
    int number = 10;

    return 0;
}
```
{: file="main.cpp" }
위 코드를 실행시키는 상황에서 `number`변수의 들어있는 값 10이 메모리 주소 `0x00000001`에 있다고 하면,<br>
`&number`의 값은 `0x00000001`이 됩니다.

 > 0x는 16진수를 나타내는 문자로 0x뒤에 있는 수가 16진수로 이루어졌다는 것을 나타냅니다.
{: .prompt-tip }

```cpp
#include <iostream>

int main() {
    int number = 10;

    std::cout << "address: " << &number;

    return 0;
}
```
{: file="main.cpp" }
```
address: 0x00000001
```
{: file="output.cpp" }

### 2-2. 포인터 자료형
포인터 자료형은 포인터가 가르킬 메모리 주소의 타입 뒤에 `*`기호가 붙은 형태로 사용됩니다.
예를 들어서 정수가 저장된 변수를 가르키는 포인터 변수를 만든다면 아래 코드처럼 되는 것이죠.

```cpp
int main() {
    int number = 10; // 정수가 저장된 변수
    int* pointer = &number; // pointer라는 포인터 변수에 number라는 변수의 메모리 값을 저장한 코드

    return 0;
}
```
위에 적힌 코드처럼 `int` 자료형이 저장된 메모리 주소를 저장하는 포인터 변수라면 `int*`로 자료형을 입력합니다.

### 2-3. * 기호
`*`기호는 포인터 자료형을 나타내는 용도 이외에도 사용됩니다.
***특정 메모리의 주소값 앞에 `*`기호를 붙힌다면 그 메모리에 있는 값이 반환***되게 됩니다.

```cpp
int main() {
    int number = 10; // number라는 정수 자료형의 변수를 선언하고 값 할당

    int* numberPointer = &number; // number 변수의 메모리 주소를 저장

    int newNumber = *numberPointer; // number 변수의 메모리가 저장된 numberPointer 포인터 변수의 메모리 주소를 바탕으로 정수 값을 가져옴

    return 0;
}
```

## 3. 뻘짓
정리하자면 아래와 같습니다.

 > &기호는 메모리에 저장된 값을 바탕으로 그 메모리의 주소를 가져옵니다.
{: .prompt-tip }

 > *기호는 포인터 변수에 저장된 메모리 주소를 바탕으로 실제 그 메모리에 있는 값을 가져옵니다.
{: .prompt-tip }

따라서 포인터에서 `&`기호와 `*`기호는 서로 반대되는 역할이라는 것을 알 수 있습니다.

그렇다면 아래 코드는 어떻게 실행될까요?

```cpp
#include <iostream>

int main() {
    int number = 10;

    std::cout << *&*&*&*&*&*&*&*&*&*&*&number;

    return 0;
}
```
{: file="main.cpp" }

정답은 ***10이 출력된다.*** 입니다.