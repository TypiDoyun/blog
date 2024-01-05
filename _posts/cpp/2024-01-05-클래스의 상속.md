---
title: "[C++] 클래스의 상속 #8"
date: 2024-01-05 19:21:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop] # TAG names should always be lowercase
---

## 1. 상속이란?
상속은 ***어떠한 클래스가 자신의 속성과 동작을 다른 클래스에게 물려주는 것을 의미*** 합니다.<br>
따라서 상속받은 클래스는 그 속성과 동작을 사용할 수 있게 되는 것이죠.

예를 들어, 사람은 동물입니다. 따라서 사람은 동물이 가지는 특성을 가지죠.<br>
따라서 숨을 쉬거나, 음식을 먹어야 한다는 점에서 사람은 동물이라는 큰 클래스의 상속을 받는 것입니다.

```cpp
#include <iostream>

class Animal {
public:
    void eat() {
        std::cout << "밥 먹는 중...\n";
    }

    void breathe() {
        std::cout << "숨쉬는 중...\n";
    }
}

class Human : public Animal {
public:
    void say() {
        std::cout << "안녕하세요 반갑습니다.\n";
    }
}
```
{: file="main.cpp" }

클래스는 상속을 받으면 ***상속받는 클래스의 생성자를 실행하고 그 이후 자신의 생성자를 실행하는 특징*** 이 있습니다.

> Human이 Animal에게 상속받는 중이므로 Animal의 생성자가 실행된 후 Human의 생성자가 실행됩니다.
{: .prompt-tip }

## 2. 다중 상속
***클래스의 상속은 제한 없이 다중적으로 사용*** 할 수 있습니다.
예를 들어, `Animal`에게 상속받는 `Human`이라는 클래스는 또 다른 클래스를 상속하는데 사용할 수 있는 것이다.

따라서 다중 상속으로 인해 상속이 연쇄적으로 일어나 ***중복 코드를 줄이는데 효과적으로 사용할 수 있다는 장점*** 이 생긴다.