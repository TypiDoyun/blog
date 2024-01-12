---
title: "[C++] 참조자란? #15"
date: 2024-01-12 22:00:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop]     # TAG names should always be lowercase
---

## 1. 참조자를 쓰는 이유
참조자는 특정 변수의 별명처럼 사용되어, 그 변수가 가르키는 메모리를 동일하게 가르킵니다.
따라서 함수의 값을 전달할 때 유용하게 사용할 수 있습니다.

## 2. 참조자의 선언
참조자의 선언은 자료형 뒤에 `&` 연산자를 붙여주면 됩니다.

```cpp
int main() {
    int number = 10;
    
    int& ref = number;

    return 0;
}
```
{: file="main.cpp" }
위 코드는 `ref`라는 참조자가 `number`를 참조하는 코드입니다.

참조자를 선언할 때에는 주의해야 할 점이 있습니다.

* 참조자의 자료형은 참조할 변수의 자료형과 같아야 합니다.
* 참조자는 선언과 동시에 초기화되어야 합니다.
* 참조자가 참조하는 대상은 변경할 수 없습니다.

 > 참조자의 값을 변경하면 참조자가 참조하는 변수의 값이 같이 변경됩니다.
{: .prompt-tip }

```cpp
#include <iostream>

using namespace std;

int main() {
    int number = 10;
    
    int& ref = number;

    ref = 30;

    cout << number;

    return 0;
}
```
{: file="main.cpp" }
```
30
```
{: file="output.txt" }

`number`를 참조하는 `ref`의 값을 30으로 수정하자 `number`값이 30으로 바뀐 것을 볼 수 있습니다.

## 3. 참조자를 함수 인수로 전달하기
참조자 또한 매개변수로 사용할 수 있습니다.

```cpp
#include <iostream>

using namespace std;

int setZero(int& value) {
    value = 0;
}

int main() {
    int number = 1234;

    setZero(number);

    cout << number;

    return 0;
}
```
{: file="main.cpp" }
```
0
```
{: file="output.txt" }

참조자를 매개변수로 사용하고 인자로 값을 넘기자 함수에서 수정한 값이 실제 인자에도 영향을 미치는 모습을 볼 수 있습니다.