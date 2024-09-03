---
title: "[Math] 유클리드 호제법과 최소공배수"
date: 2024-06-11 14:32:00 +/-TTTT
categories: [math, algorithm]
tags: [math, algorithm, euclidean]   # TAG names should always be lowercase
---

{% include math.html %}

## 1. 최대공약수의 직관적 이해
$_
a=2^{2}\times 3^{3}\times 5^{2}
_$

$_
b=2\times 3^{2}\times 5^{4}
_$

라고 한다면, 아래 식의 값은 얼마가 될까요?<br>
$_
gcd(a,b)
_$

우선, 공약수에 대해서 간단하게 짚고 넘어갑시다.<br>
공약수란, 두 개 이상의 수가 공통적으로 가지는 약수입니다.<br>
따라서 **$a$와 $b$의 공약수로 $a$또는 $b$를 나누었을 때는 자연수가 나와야합니다.**<br>
$_
    |\frac{a}{cd(a,b)}|\in\mathbb{N}
_$

$_
    |\frac{b}{cd(a,b)}|\in\mathbb{N}
_$

(**음의 약수도 있기 때문에 절댓값 기호를 붙여주었습니다.**)<br>
그렇다면, $a$와 $b$의 공약수는 $a$와 $b$를 나누어도 양의 정수가 나와야 합니다.<br>
따라서, $a$와 $b$를 소인수분해한 각각의 항들의 차수가 $a$와 $b$의 차수를 초과하지 않게,<br>
즉, 두 수의 소인수들의 최소 차수보다 작게 구성한다면 공약수를 찾을 수 있습니다.<br>

예를 들어, 맨 위에 적힌 식에서 항이 $2$인 경우 $a$의 최대 차수는 $2$이고, $b$의 최대 차수는 $1$입니다.<br>
따라서 $a$와 $b$의 공약수를 $c$라고 가정한다면, **$c$의 소인수 $2$는 차수가 $1$ 이하이어야 한다는 것입니다.<br>
따라서 $c$의 소인수 $2$의 차수는 $1$이하의 숫자가 됩니다.<br>

$_
    c=2^{1}\times 3^{z_2}\times 5^{z_3}
_$

위와 같은 방법을 $c$의 모든 소인수에 반복한다면,<br>
**$c$의 소인수 $3$은 차수가 $2$이하이며, $5$는 차수가 $2$이하이어야 한다는 것을 알 수 있습니다.**<br>

그렇다면 최대공약수란 이러한 조건을 만족시키면서 가장 큰 수라는 것입니다.<br>
따라서, $a$의 소인수 $p$의 차수가 $x$이고 $b$의 소인수 $p$의 차수가 $y$라면,<br>
그 두 수의 최대공약수의 소인수 $q$의 차수 $z$는 다음과 같이 나타낼 수 있습니다.<br>
$_
    z = min(x, y)
_$

조금 더 구체적으로 설명하면,<br>
$_
    a=2^{x_1}\times 3^{x_2}\times 5^{x_3}\times 7^{x_4}\times\cdot\cdot\cdot\times p^{x_n}
_$

$_
    b=2^{y_1}\times 3^{y_2}\times 5^{y_3}\times 7^{y_4}\times\cdot\cdot\cdot\times p^{y_n}
_$

다음과 같은 두 수 $a$, $b$의 최대공약수 $gcd(a,b)$는 다음과 같이 정의할 수 있습니다.<br>

$_
    gcd(a,b)=2^{min(x_1,y_1)}\times 3^{min(x_2,y_2)}\times 5^{min(x_3,y_3)}\times 7^{min(x_4,y_4)}\times\cdot\cdot\cdot\times p^{min(x_n,y_n)}
_$

## 2. 최소공배수의 직관적 이해

공배수는 공약수와는 반대로 **$a$와 $b$의 공배수를 $a$또는 $b$로 나누었을 때 자연수가 나와야 합니다.**<br>
따라서 $a$와 $b$의 **공배수 $c$**는 $a$와 $b$의 소인수들의 최대 차수로 구성되어야 합니다.<br>

$_
    a=2^{2}\times 3^{3}\times 5^{2}
_$

$_
    b=2\times 3^{2}\times 5^{4}
_$

위 값을 예시로 한다면,<br>

공배수 $c$의 소인수 $2$는 차수가 2 이상이어야 하며, 3의 차수는 3 이상, 5의 차수는 4이상이어야 합니다.<br>

최소공배수는 이러한 수들 중 가장 작은 수 이므로,<br>
그 두 수의 최소공배수를 구성하는 $n$의 차수는 다음과 같습니다.<br>
$_
    z = max(x, y)
_$

조금 더 구체적으로 설명한다면,<br>

$_
    a=2^{x_1}\times 3^{x_2}\times 5^{x_3}\times 7^{x_4}\times\cdot\cdot\cdot\times p^{x_n}
_$

$_
    b=2^{y_1}\times 3^{y_2}\times 5^{y_3}\times 7^{y_4}\times\cdot\cdot\cdot\times p^{y_n}
_$

다음과 같은 두 수 $a$, $b$의 최대공약수는 아래와 같이 정리할 수 있습니다.<br>

$_
    lcm(a,b)=2^{max(x_1,y_1)}\times 3^{max(x_2,y_2)}\times 5^{max(x_3,y_3)}\times 7^{max(x_4,y_4)}\times\cdot\cdot\cdot\times p^{max(x_n,y_n)}
_$

## 3. 유클리드 호제법

유클리드 호제법이란 최대공약수를 빠르게 구하는 알고리즘을 말합니다.<br>
유클리드 호제법의 공식은 다음과 같습니다.<br> 
$_
    gcd(a,b)=gcd(b,a\mod b)
_$

따라서 $9$와 $6$의 최대공약수는 위에 식을 이용하여 아래처럼 간단하게 구할 수 있습니다.<br>
$_
    gcd(9,6)\newline=gcd(6,3)\newline=gcd(3,0)
_$

어떤 수와 $0$의 최대공약수는 자기 자신이기 때문에 $3$이 최대공약수가 됩니다.<br>

## 4. 최대공약수를 이용한 최소공배수의 계산

$_
    a=2^{x_1}\times 3^{x_2}\times 5^{x_3}\times 7^{x_4}\times\cdot\cdot\cdot\times p^{x_n}
_$

$_
    b=2^{y_1}\times 3^{y_2}\times 5^{y_3}\times 7^{y_4}\times\cdot\cdot\cdot\times p^{y_n}
_$

다음과 같은 $a$와 $b$가 있다고 했을 때, 두 수의 최대공약수는 아래와 같습니다.<br>

$_
    gcd(a,b)=2^{min(x_1,y_1)}\times 3^{min(x_2,y_2)}\times 5^{min(x_3,y_3)}\times 7^{min(x_4,y_4)}\times\cdot\cdot\cdot\times p^{min(x_n,y_n)}
_$

이 때 한가지 간단한 포인트가 있습니다.<br>
**바로, 어떤 수 $x$와 $y$가 있을 때 그 두 수를 더한 값에서 두 수 중 더 작은 수를 빼면 두 수중 큰 수가 나오게 된다는 것입니다.**<br>

$_
    max(x,y)=x+y-min(x,y)
_$

$_
    min(x,y)=x+y-max(x,y)
_$


따라서 최대공약수를 의미하는 식에서 모든 항의 지수만 $max(a_n,b_n)$으로 만들어준다면,<br>
최소공배수가 되기 때문에 간단하게 최소공배수를 구할 수 있게됩니다.<br>

$_
    a \times b=2^{x_1+y_1}\times 3^{x_2+y_2}\times 5^{x_3+y_3}\times 7^{x_4+y_4}\times\cdot\cdot\cdot\times p^{x_n+y_n}
_$
    
$_
    \frac{a\times b}{gcd(a,b)}=2^{x_1+y_1-min(x_1,y_1)}\times 3^{x_2+y_2-min(x_2,y_2)}\times 5^{x_3+y_3-min(x_3,y_3)}\times 7^{x_4+y_4-min(x_4,y_4)}\times\cdot\cdot\cdot\times p^{x_n+y_n-min(x_n,y_n)}\newline=2^{max(x_1,y_1)}\times 3^{max(x_2,y_2)}\times 5^{max(x_3,y_3)}\times 7^{max(x_4,y_4)}\times\cdot\cdot\cdot\times p^{max(x_n,y_n)}
_$

따라서,<br>

$_
    lcm(a,b)=\frac{a\times b}{gcd(a,b)}
_$

이렇게 최대공약수를 이용하여 최소공배수를 구할 수 있습니다.<br>