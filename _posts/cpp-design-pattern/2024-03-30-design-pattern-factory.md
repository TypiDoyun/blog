---
title: "[C++ / Design Pattern] 팩토리 패턴 #3"
date: 2024-03-30 23:27:00 +/-TTTT
categories: [design-pattern, cpp]
tags: [design-pattern, cpp]   # TAG names should always be lowercase
---

## 1. 팩토리 패턴이란?

`Pizza`라는 클래스가 있다고 가정해봅시다.

```cpp
class Pizza {
public:
    
};
```
{: file="pizza.h"}

하지만 피자가게에 가서 그냥 **"피자 주세요."** 라고 하지는 않습니다.<br>
**"페퍼로니 피자 주세요."** 또는 **"치즈 피자 주세요."** 와 같이 조금더 구체화된 피자를 말하죠.<br>
이와 같이 피자는 **"도우 위에 소스와 토핑 등을 올려 구운 음식"**을 축약한 추상적 개념입니다.<br>

따라서 `Pizza`라는 클래스 또한 추상 클래스에 속한다고 분류할 수 있죠.
`피자는 토핑을 올리고 굽는다.` 라는 점을 기억하면, `Pizza`라는 추상 클래스의 함수로는
`placeTopping`과 `bake`가 있어야겠네요.

```cpp
class Pizza {
public:
    virtual ~Pizza() = default;
    virtual void placeTopping() = 0;
    virtual void bake() = 0;
}
```
{: file="pizza.h"}

그렇다면 이제 조금더 구체화된 클래스를 만들어보겠습니다.

```cpp
#include "pizza.h"
#include <iostream>

using namespace std;

class PepperoniPizza : public Pizza {
public:
    void placeTopping() {
        cout << "치즈를 올렸습니다.\n";
        cout << "페퍼로니를 올렸습니다.\n";
    }

    void bake() {
        cout << "피자를 섭씨 190도 15분간 구웠습니다.\n";
    }
};

class CheesePizza : public Pizza {
public:
    void placeTopping() {
        cout << "치즈를 올렸습니다.\n";
    }

    void bake() {
        cout << "피자를 섭씨 210도 13분간 구웠습니다.\n";
    }
};
```
{: file="other-pizza.h" }

이제 피자를 주문하는 코드를 만들어 보겠습니다.

```cpp
#include <memory>
#include "other-pizza.cpp"

int main() {
    string pizzaType = "cheese";

    unique_ptr<Pizza> pizza;

    if (pizzaType == "pepperoni") pizza = make_unique<PepperoniPizza>();
    else if (pizzaType == "cheese") pizza = make_unique<CheesePizza>();

    pizza->placeTopping();
    pizza->bake();
}
```
{ file="main.cpp" }
```
치즈를 올렸습니다.
피자를 섭씨 210도 13분간 구웠습니다.
```
{: file="output.txt" }

지금 코드는 요청, 생성이 모두 한 코드에 모여 있습니다.<br>
따라서 팩토리 디자인 패턴을 이용해서 생성 부분을 분리시켜 조금 더 코드를 구조적이게 만들 수 있습니다.<br>

```cpp
#include <string>
#include "other-pizza.h"

class SimplePizzaFactory {
public:
    Pizza& createPizza(string pizzaType) {
        unique_ptr<Pizza> pizza;

        if (pizzaType == "pepperoni") pizza = make_unique<PepperoniPizza>();
        else if (pizzaType == "cheese") pizza = make_unique<CheesePizza>();
        else throw "Unknown pizza type";

        pizza->placeTopping();
        pizza->bake();

        Pizza& pizzaRef = *pizza;

        return pizzaRef;
    }
};
```
{: file ="pizza-factory.h" }
```cpp
#include <iostream>
#include <memory>
#include <string>
#include "pizza-factory.h"

int main() {
    string pizzaType = "cheese";

    SimplePizzaFactory pizzaFactory;
    Pizza& pizza = pizzaFactory.createPizza(pizzaType);
}
```
{: file="main.cpp" }
```
치즈를 올렸습니다.
피자를 섭씨 210도 13분간 구웠습니다.
```
{: file="output.txt" }

다음과 같이 팩토리 디자인 패턴을 사용하면 프로그램을 조금 더 구조화 시킬 수 있습니다.