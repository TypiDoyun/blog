---
title: "[C++] 프랜드 함수란? #22"
date: 2024-01-19 22:39:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop]   # TAG names should always be lowercase
---

## 1. 프렌드 함수의 필요성
프렌드 함수는 `private` 속성이나 `protecte 속성에 멤버 함수가 아닌 함수가 접근하기 위해 사용됩니다.

## 2. 프렌드 함수 사용법
프렌드 함수는 `friend` 키워드를 붙여 아래와 같이 사용할 수 있습니다.

```cpp
#include <iostream>
#include <string>

using namespace std;

class Human {
private:
    int height;

public:
    Human(int age, string name, int height) {
        this->age = age;
        this->name = name;
        this->height = height;
    }

    int age;
    string name;

    friend void say(const Human& human) {
        cout << "안녕하세요 제 이름은 " << human.name << "이며, 나이는 " << human.age << "살 입니다. 키는 " << human.height << "cm입니다.";
    }
};

int main() {
    Human human(19, "김도윤", 180);

    say(human);
}
```
{: file="main.cpp" }
```
안녕하세요 제 이름은 김도윤이며, 나이는 19살 입니다. 키는 180cm입니다.
```
{: file="output.txt" }

위 코드처럼 `friend` 키워드를 사용하면 멤버함수가 아니더라도 `private` 속성에 접근할 수 있습니다.