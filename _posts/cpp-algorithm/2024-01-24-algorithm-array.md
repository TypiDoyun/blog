---
title: "[C++ / Algorithm] 배열 #4"
date: 2024-01-24 22:50:00 +/-TTTT
categories: [algorithm, cpp]
tags: [algorithm, cpp]   # TAG names should always be lowercase
---

## 1. 배열의 특징

배열은 선형 자료구조로 같은 자료형의 데이터들을 메모리에 연속적으로 저장합니다.<br>
배열안에 저장된 각각의 데이터들은 **`요소`**라고 불리며, 요소들의 순서를 가르키는 것을 **`인덱스`**라고 합니다.

배열은 인덱스로 요소에 접근해 특정 요소를 읽는 시간 복잡도가 굉장히 빠릅니다. **`O(N)`**<br>

또한, 배열은 정적 자료구조로 요소를 추가로 더 넣는 작업은 할 수 없습니다.

----

## 2. C++에서의 배열

C++에서는 아래와 같이 배열을 사용합니다.

```cpp
#include <iostream>

using namespace std;

int arr[5] = { 30, 20, 0, 500, 10 };

int main() {
    int sum = arr[0] + arr[1];

    cout << sum;

    return 0;
}
```
{: file="main.cpp" }
```
50
```
{: file="output.txt" }

배열의 **`인덱스`**는 0부터 시작하며 첫 번째 요소의 **`인덱스`**는 0이 됩니다.
따라서 **`arr[0] + arr[1]`**의 값은 50이 됩니다.

## 3. 배열의 장단점

### 3-1. 배열의 장점

* 인덱스를 이용하기 때문에 배열의 길이가 아무리 길더라도 모든 요소에 **`O(1)`**의 시간 복잡도로 접근할 수 있습니다.
* 사용하기 간편합니다.

----

### 3-2. 배열의 단점

* 정적 자료구조로 길이를 변경할 수 없습니다.
* 배열의 중간에 값을 넣거나 삭제하는 경우 뒤에 있는 모든 요소를 한 칸씩 이동해야 하므로 시간 복잡도가 높아지게 됩니다.