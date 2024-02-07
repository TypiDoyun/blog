---
title: "[C++ / Algorithm] 피보나치 수열과 동적 계획법 #15"
date: 2024-02-07 21:47:00 +/-TTTT
categories: [algorithm, cpp]
tags: [algorithm, cpp]   # TAG names should always be lowercase
---

## 1. 피보나치 수열이란?

피보나치 수열은 ***앞에 있는 2개의 항을 더해서 다음 항을 만들어내는 유명한 수열***입니다.<br>
피보나치 수열엔 몇가지 규칙이 있는데 그 중 하나는 ***첫 번째 항과 두 번째 항은 0과 1***이어야 한다는 점입니다.

----

## 2. 재귀함수를 이용한 피보나치 수열

프로그램에서 피보나치 수열의 항을 구하는 방법은 아주 다양합니다.<br>
그 중에선 재귀함수를 이용하는 방법도 있습니다.

다음 코드는 재귀함수를 이용하여 피보나치 수열을 구하는 C++ 코드입니다.

```cpp
#include <iostream>

using namespace std;

int fibonacci(int);

int main() {
    cout << fibonacci(5);
}

int fibonacci(int n) {

    if (n <= 0) return 0;

    if (n == 1) return 0;
    if (n == 2) return 1;

    return fibonacci(n - 1) + fibonacci(n - 2);
}
```
{: file="main.cpp" }
```
3
```
{: file="output.txt" }

위 코드와 같이 재귀함수를 이용한다면 간단하게 피보나치 수열을 구할 수 있습니다.<br>
하지만 위 코드에는 한 가지 문제점이 있습니다.<br>
바로 똑같은 피보나치 수열의 항을 여러번 구한다는 점입니다.

아래 코드를 본다면 알 수 있습니다.

```cpp
#include <iostream>

using namespace std;

int fibonacci(int);

int main() {
    cout << fibonacci(5);
}

int fibonacci(int n) {

    printf("fibonacci(%d) is called.\n", n);

    if (n <= 0) return 0;

    if (n == 1) return 0;
    if (n == 2) return 1;

    return fibonacci(n - 1) + fibonacci(n - 2);
}
```
{: file="main.cpp" }
```
fibonacci(5) is called.
fibonacci(4) is called.
fibonacci(3) is called.
fibonacci(2) is called.
fibonacci(1) is called.
fibonacci(2) is called.
fibonacci(3) is called.
fibonacci(2) is called.
fibonacci(1) is called.
3
```
{: file="output.txt" }

위 코드처럼 원래라면 한 번만 구해도 되지만 재귀함수를 사용한다는 이유로 똑같은 작업을 여러번 실행하고 있습니다.<br>
하지만 이 때 **`다이나믹 프로그래밍(Dynamic Programming)`**의 **`메모이제이션(Memoization)`** 기법을 사용한다면,<br>
피보나치 수열을 구하는데 걸리는 시간을 효과적으로 단축시킬 수 있습니다.

## 2. 메모이제이션을 활용한 피보나치 수열

피보나치 수를 구할 때마다 특정한 배열에 그 값을 기억해놓고 나중에 다시 필요할 때마다<br>
그 값을 꺼내 쓴다면 훨씬 빠르게 실행할 수 있지 않을까요?<br>
그러한 방법을 사용한 것이 **`메모이제이션(Memoization)`** 기법입니다.

아래 코드는 **`메모이제이션(Memoization)`** 을 사용해서 피보나치 수열을 구하는 코드입니다.

```cpp
#include <iostream>
#include <vector>

using namespace std;

vector<int> series = { 0, 1 };

int fibonacci(int);

int main() {
    cout << fibonacci(8);
}

int fibonacci(int n) {
    if (n <= 0) return 0;
    
    for (int i = 2; i < n; i++) {
        if (series.size() > i) continue;
        
        series.push_back(series[i - 1] + series[i - 2]);
    }
    
    return series[n - 1];
}
```
{: file="main.cpp" }
```
13
```
{: file="output.txt" }

위 코드를 사용한다면 n번째 피보나치 수를 구하는 데 n번의 반복만 하면 되기 때문에 훨씬 빨라진다는 장점이 생깁니다.