---
title: "[C++] Hello World! #2"
date: 2023-12-31 21:19:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop]     # TAG names should always be lowercase
---

## 1. C++과 친해지기
모든 프로그래밍 언어를 배움에 있어서<br>
가장 먼저 해봐야하는 것은 메시지 출력입니다.

> ~~메시지를 출력하는 코드 하나만으로 그 언어의 난이도가 대략 짐작이 가기 때문이죠.~~
{: .prompt-tip }

----

## 2. Hello World!

### 2-1. C
C언어에서는 아래와 같이 `stdio.h`라는 헤더 파일을 불러와 출력을 합니다.
```c
#include <stdio.h>

int main() {
    printf("Hello World!");

    return 0;
}
```
{: file="main.c" }
```
Hello World!
```
{: file="output.txt" }

### 2-2. C++

하지만 C++이라고 해서 많이 다를 것은 없습니다.<br>
C++에서도 똑같이 작성해도 되지만, C++에서 사용할 수 있는 헤더 파일이 있습니다.<br>
바로 `iostream`이죠 아래 코드가 C++의 출력 코드입니다.
```cpp
#include <iostream>

int main() {
    std::cout << "Hello World!";

    return 0;
}
```
{: file="main.cpp"}
```
Hello World!
```
{: file="output.txt" }
아마 C언어에서 비트 시프트를 배우신 분들은 더 혼란스러우실 수 있습니다.<br>
***"`std::cout`은 뭐고 또 저 이상한 시프트 연산은 뭐지?"*** 이렇게요. 

하지만 저 코드는 비트 시프트랑은 느낌이 다릅니다.<br>
코드 자체를 대충 보자면 `std::cout`에 `<<` 연산자를 쓰면 그 뒤에 있는 값이 출력되는 것 같습니다.<br>
바로 테스트 해보죠.

```cpp
#include <iostream>

int main() {
    std::cout << "Hello" << " " << "World!";

    return 0;
}
```
{: file="main.cpp"}
```
Hello World!
```
{: file="output.txt"}

실행 결과는 예상한 것처럼 `<<` 연산을 사용한 값들이 연결되어서 나오고 있습니다.<br>
따라서 `std::cout`은 C언어의 `printf`와 비슷하다고 볼 수 있습니다.<br>