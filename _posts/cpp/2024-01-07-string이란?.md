---
title: "[C++] string이란? #10"
date: 2024-01-07 20:39:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop] # TAG names should always be lowercase
---

## 1. C언어 스타일의 문자열
C언어는 문자열을 저장하려면 직접 배열의 길이를 지정해주어야 했습니다.

```cpp
#include <stdio.h>

char sentence[100] = "Hello World!";

int main() {
    printf("%s", string);

    return 0;
}
```
{: file="main.cpp" }

이러한 방식은 길이가 변할 수 있는 문자열을 다룰 때는 사용하기 까다롭다는 단점이 있습니다.

----

## 2. C++의 문자열
C++에서는 `string`이라는 헤더파일을 사용해 훨씬 간단하게 문자열을 다룰 수 있습니다.

### 2-1. 생성과 출력하기

```cpp
#include <iostream>
#include <string>

string sentence = "Hello World!";

int main() {
    std::cout << sentence;

    return 0;
}
```
{: file="main.cpp" }
```
Hello World!
```
{: file="output.txt" }

`string`으로 생성된 문자열은 `std::cout`을 사용해서 출력할 수 있습니다.<br>
만약 `printf`를 사용하여 출력하려 한다면 `c_str()`메서드를 사용해서 C언어 스타일읨 문자열로 변경해야합니다.

```cpp
#include <iostream>
#include <string>

string sentence = "Hello World!";

int main() {
    printf("%s", sentence.c_str());

    return 0;
}
```
{: file="main.cpp" }
```
Hello World!
```
{: file="output.txt" }

----

### 2-2. 인덱스로 접근하기
C++의 문자열 또한 인덱스를 사용할 수 있습니다.

```cpp
#include <iostream>
#include <string>

string sentence = "Hello World!";

int main() {
    printf("%c", sentence[0]);

    return 0;
}
```
{: file="main.cpp" }
```
H
```
{: file="output.txt" }

----

## 3. C++ 문자열 입력받기
우선, C++의 문자열을 `scanf`으로 입력받는 것은 불가능합니다.
따라서 아래 방법처럼 `cin`을 사용해서 입력받아야 합니다.

```cpp
#include <iostream>
#include <string>

string input;

int main() {
    std::cin >> input;

    std::cout << input;

    return 0;
}
```
{: file="main.cpp" }
```
TypiDoyun
```
{: file="input.txt" }
```
TypiDoyun
```
{: file="output.txt" }