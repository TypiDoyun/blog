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
{: file="main.cpp"}

하지만 피자가게에 가서 그냥 **"피자 주세요."** 라고 하지는 않습니다.<br>
**"페퍼로니 피자 주세요."** 또는 **"치즈 피자 주세요."** 와 같이 조금더 구체화된 피자를 말하죠.<br>
이와 같이 피자는 **"도우 위에 소스와 토핑 등을 올려 구운 음식"**을 축약한 추상적 개념입니다.<br>

따라서 `Pizza`라는 클래스 또한 