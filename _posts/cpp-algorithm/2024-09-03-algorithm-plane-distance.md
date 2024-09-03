---
title: "[C++ / Algorithm] 무한한 평면과 점 사이의 거리 #24"
date: 2024-09-03 11:31:00 +/-TTTT
categories: [algorithm, cpp]
tags: [algorithm, cpp, sdf]   # TAG names should always be lowercase
---

{% include math.html %}

## 1. 평면의 방정식

평면의 방정식은 3차원 공간에 존재하는 평면을 나타내는 방정식입니다.<br>
$_
    ax + by + cz + d = 0
_$

평면의 방정식의 특징은 **<u>그라디언트가 법선 방향을 가르킨다는 것</u>**입니다.<br>
이 이유는 그라디언트의 정의를 이해하면 그 이유를 쉽게 알 수 있습니다.<br>
**<u>그라디언트는 공간에서 값이 커지는 방향을 가르킨다는 특징</u>**이 있습니다.<br>
따라서, 평면의 방정식은 값이 0인 지점들이 모인 것으로,<br>
평면이 나누는 2개의 공간 중 법선 벡터가 가르키는 공간은 값이 커져야하므로<br>
$ ax + by + cz + d $의 값이 양수가 되는 공간이며,<br>
법선 벡터의 반대편 공간은<br>
$ ax + by + cz + d $의 값이 음수가 되는 공간입니다.

## 2. 평면의 방정식을 이용한 거리 함수

우선, **<u>거리를 계산할 위치</u>** $p$와, **<u>평면의 법선벡터</u>** $n$을 입력받아야 합니다.<br>
원점을 지나는 평면을 기준으로 거리를 측정할 것이기 때문에,<br>
$z$절편을 입력받을 필요가 없습니다.<br>

$_
\vec{p} = \begin{bmatrix}
p_{x} \newline
p_{y} \newline
p_{z}
\end{bmatrix},\space \vec{n} = \begin{bmatrix}
n_{x} \newline
n_{y} \newline
n_{z} 
\end{bmatrix}
_$

이 값을 기준으로 원점을 지나는 평면의 방정식은 다음과 같습니다.<br>

$_
n_{x}x + n_{y}y + n_{z}z = 0
_$

이제 이 방정식을 이용하여 거리를 계산하는 함수를 정의해보겠습니다.<br>

우선, 평면 $A$와 $p$사이를 잇는 벡터의 길이가 거리라는 것을 생각할 수 있습니다.<br>
이러한 벡터를 $l$이라고 하겠습니다.<br>

이때, $l$의 크기는 알 수 없지만, **<u>$A$와 수직이라는 성질을 이용</u>**하여 방향을 알 수 있습니다.<br>
따라서, $l$은 $n$의 방향과 같은 방향을 가집니다.<br>
이를 수식으로 나타낸다면 다음과 같습니다.<br>

$_
\vec{l} = k\vec{n}
_$

이러한 벡터 $l$는 평면 $A$위의 임의의 점 $q$와 $p$를 잇는 벡터이므로 다음과 같이도 표현할 수 있습니다<br>

$_
\vec{l} = \vec{p} - \vec{q}
_$

$_
k\vec{n} = \vec{p} - \vec{q}
_$

이때 $q$는 평면 $A$위의 임의의 점이므로, $A$의 방정식을 만족해야합니다.<br>
따라서, $q$를 다음과 같이 표현할 수 있습니다.<br>

$_
\definecolor{color1}{RGB}{252, 179, 30}
\definecolor{color2}{RGB}{203, 111, 24}
\definecolor{color3}{RGB}{65, 75, 14}
\begin{align} \label{eq1}
\begin{split}
\vec{q} &= \vec{p} - k\vec{n} \newline
&= \begin{bmatrix}
    \color{color1}p_{x} - k \cdot n_{x} \newline
    \color{color2}p_{y} - k \cdot n_{y} \newline
    \color{color3}p_{z} - k \cdot n_{z}
    \end{bmatrix}
\end{split}
\end{align}
_$

$_
n_{x}(\textcolor{color1}{p_{x} - k \cdot n_{x}}) + n_{y}(\textcolor{color2}{p_{y} - k \cdot n_{y}}) + n_{z}(\textcolor{color3}{p_{z} - k \cdot n_{z}}) = 0 
_$

$_
n_{x}p_{x} - k \cdot n_{x}^{2} + n_{y}p_{y} - k \cdot n_{y}^{2} + n_{z}p_{z} - k \cdot n_{z}^{2} = 0
_$

$_
n_{x}p_{x} + n_{y}p_{y} + n_{z}p_{z} = k \cdot (n_{x}^{2} + n_{y}^{2} + n_{z}^{2})
_$

$_
k = \frac{n_{x}p_{x} + n_{y}p_{y} + n_{z}p_{z}}{n_{x}^{2} + n_{y}^{2} + n_{z}^{2}}
_$

이제 $k$를 구했으므로, $l$의 크기를 구할 수 있습니다.<br>

$_
\begin{align} \label{eq2}
\begin{split}
distance &= k \cdot |\vec{n}| \newline
&= \frac{n_{x}p_{x} + n_{y}p_{y} + n_{z}p_{z}}{n_{x}^{2} + n_{y}^{2} + n_{z}^{2}} \cdot \sqrt{n_{x}^{2} + n_{y}^{2} + n_{z}^{2}} \newline
&= \frac{n_{x}p_{x} + n_{y}p_{y} + n_{z}p_{z}}{\sqrt{n_{x}^{2} + n_{y}^{2} + n_{z}^{2}}} \newline
&= \frac{\vec{n} \cdot \vec{p}}{|\vec{n}|}
\end{split}
\end{align}
_$

이제 이를 C++ 코드로 구현해보겠습니다.<br>

## 3. C++ 코드

```cpp
#include <iostream>
#include <cmath>

struct Vector3
{
    float x, y, z;
};

float dot(Vector3 a, Vector3 b)
{
    return a.x * b.x + a.y * b.y + a.z * b.z;
}

float length(Vector3 a)
{
    return sqrt(a.x * a.x + a.y * a.y + a.z * a.z);
}

float sdPlane(Vector3 p, Vector3 n) {
    return dot(p, n) / length(n);
}

int main() {
    Vector3 p = {0, 5, 0}; // 점의 위치
    Vector3 n = {0, 1, 0}; // 평면의 법선벡터

    std::cout << sdPlane(p, n) << std::endl; // 5

    return 0;
}
```
{: file="sdPlane.cpp"}

```
{: file="sdPlane.cpp"}

