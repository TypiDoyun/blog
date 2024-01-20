---
title: "[C++] 반복자란? #23"
date: 2024-01-20 21:17:00 +/-TTTT
categories: [cpp, basic]
tags: [cpp, oop]   # TAG names should always be lowercase
---

## 1. 반복자란?
반복자는 컨테이너에 저장된 값들을 순차적으로 순회해주는 객체입니다.<br>
반복자는 이전 블로그에서 다룬 범위 기반 반복문에서도 사용됩니다.<br>
따라서 범위 기반 반복문은 반복자가 존재하는 객체에만 사용할 수 있습니다.

## 2. 반복자 만들기
반복자는 개념만 이해하고 넘어가는 경우가 대부분이지만,<br>
이 블로그에서는 반복자를 생성해볼 예정입니다.

반복자는 대부분의 STL 컨테이너가 가지고 있지만,<br>
자신만의 컨테이너를 만들 때는 반복자를 만드는 것이 유용하기 때문입니다.

반복자의 구조는 반복자안에 노드가 존재하는 방식으로 구현할 것입니다.

```cpp
template <typename T>
class Node {
public:
	T data;
	Node<T>* next;

	Node(T data, Node<T>* next) {
		this->data = data;
		this->next = next;
	}
	
	bool operator==(const Node& node) {
		return data == node.data && next == node.next;
	}
}
```
{: file="node.cpp"}

기본적인 노드를 생성하고 반복자를 생성합니다.<br>
반복자는 가리키는 요소의 값에 접근할 수 있어야하고,<br>
대입, 관계, 증가 연산자가 필요합니다.<br>
따라서 연산자 오버로딩이 필요합니다.

```cpp
template <typename T>
class CustomIterator {
public:
	Node<T>* currentNode;

	CustomIterator(Node<T>* node) {
		currentNode = node;
	}

	T& operator*() {
		return currentNode->data;
	}

	CustomIterator operator++() {
		currentNode = currentNode->next;

		return this;
	}

	bool operator==(const CustomIterator& ref) {
		return currentNode == ref.currentNode;
	}
	
	bool operator!=(const CustomIterator& ref) {
		return currentNode != ref.currentNode;
	}
}
```
{: file="custom-iterator.cpp"}

위 코드처럼 각각의 연산자를 오버로딩해서 반복자를 구현할 수 있습니다.