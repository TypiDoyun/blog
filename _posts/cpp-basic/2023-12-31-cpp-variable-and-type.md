---
title: "[C++] 변수와 자료형 #3"
date: 2023-12-31 21:42:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop] # TAG names should always be lowercase
---

## 1. 변수 선언

**프로그래밍 언어에서 변수란 값을 저장하는 공간을 의미**합니다.<br>
따라서 변수가 정말 중요하죠.

C++에서 변수를 선언하는 방법은 아래와 같습니다.

```cpp
int main() {
    int myVariable;

    return 0
}
```

{: file="main.cpp" }
위 코드에서 **`int`는 공간이 무슨 값을 저장할지 정하는 역할**입니다.<br>
흔히 `자료형`이라고 합니다. 따라서 정수를 저장하고 싶다면 `int`<br>
실수를 저장하고 싶다면 `float` 또는 `double`을 쓸 수 있습니다.<br>

> 더 많은 자료형은 아래에서 설명드리겠습니다.
> {: .prompt-info }

그리고 `myVariable`은 제가 지정한 변수의 이름입니다.<br>
앞으로 저 변수는 선언되었을 때 설정된 이름으로 사용하게 됩니다.

## 2. 값 할당하기

값이 저장될 공간을 만들었으면 이제 값을 저장해야겠죠.<br>
C++은 이때 대입 연산자 `=`을 사용합니다.<br>
여기서 말하는 `=`은 좌변과 우변이 같다는 이야기가 아니라.<br>
**우변의 값을 좌변에 넣겠다는 의미입니다.**

```cpp
int main() {
    int myVariable;
    myVariable = 64;

    return 0
}
```

{: file="main.cpp" }
위 코드를 실행하면 아무것도 나오지는 않지만 컴퓨터 속 메모리 어딘가에 64라는 정수 값이 저장된겁니다.

> 변수을 선언하고 값을 할당하지 않으면 쓰레기 값이 남게 됩니다.<br>
> 쓰레기 값은 프로그램의 의도치 않은 동작을 유발시키므로 변수는 반드시 값을 할당 후 사용해야합니다.
> {: .prompt-warning }

## 3. 변수의 사용

변수에 값을 저장한 후 사용하려면 어떻게 해야할까요.<br>
방법은 변수의 이름을 적어주면 끝입니다.

```cpp
#include <iostream>

int main() {
    int myVariable;
    myVariable = 64;

    std::cout << myVariable;

    return 0;
}
```

{: file="main.cpp" }

```
64
```

{: file="output.txt" }

하지만 변수를 사용할 때 주의해야할 점이 있습니다.<br>
**_변수는 사용할 수 있는 범위에 제한이 있습니다._**

### 3-1. 전역 변수

`전역 변수`는 이름처럼 **코드 전역에서 사용할 수 있는 변수**입니다.<br>
사용하는 위치가 어디가 되었든 항상 사용할 수 있습니다.

```cpp
#include <iostream>

int globalVariable = 8;

int main() {
    std::cout << globalVariable;

    return 0;
}
```

{: file="main.cpp" }
`전역 변수`는 코드의 최상단 즉, **중괄호가 쳐져있지 않은 곳에서 선언된 변수를 의미**합니다.<br>
따라서 변수의 사용 범위는 **중괄호와 같이 코드 블록에 따라서 결정된다는 사실**을 알 수 있습니다.

### 3-2. 지역 변수

`지역 변수`는 이름처럼 **특정 지역, 특정 코드 블록에서만 사용할 수 있는 변수**입니다.<br>
따라서 `지역 변수`는 코드 블록 내부에서 선언되어져 있습니다.

```cpp
#include <iostream>

int main() {
    int myVariable = 32;
    std::cout << myVariable;

    {
        int otherVariable = 16;
        std::cout << otherVariable;
    }

    return 0;
}
```

{: file="main.cpp" }
위 코드처럼 `otherVariable`은 한 단계 더 깊은 코드 블록에서 선언 되어서<br>
코드 블록 밖에서는 사용할 수 없습니다. 반대로 `otherVariable`이 선언된 코드 블록 안에서는<br>
`myVariable`변수에 접근할 수 있습니다.

## 자료형

**자료형이란 값의 유형을 말합니다.**<br>
예를 들어서 정수를 저장하고 싶다면 `int`, 실수를 저장하고 싶다면 `float`과 `double`<br>
문자를 저장하고 싶다면 `char`와 같은 자료형이 있죠.

```cpp
#include <iostream>

int main() {
    int number = 3;
    double pi = 3.141592;
    char character = 'a';

    return 0;
}
```

{: file="main.cpp" }
이처럼 C++은 변수에 자료형이라는 것을 정해서 **특정 유형의 데이터만 들어갈 수 있게 조절**합니다.
