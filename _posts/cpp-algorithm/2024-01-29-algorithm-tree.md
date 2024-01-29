---
title: "[C++ / Algorithm] 트리 #8"
date: 2024-01-29 21:07:00 +/-TTTT
categories: [algorithm, cpp]
tags: [algorithm, cpp]   # TAG names should always be lowercase
---

## 1. 트리란?

트리 자료구조는 노드들이 나뭇가지처럼 연결된 비선형 자료구조입니다.<br>
맨 위에 있는 루트 노드를 기준으로 뻗어나가는 노드들이 각각의 노드를 가지고 있는 계층형 구조이기도 합니다.<br>
컴퓨터의 폴더 구조가 트리와 매우 유사하다는 점이 있습니다.

----

## 2. 트리 자료구조에서 사용되는 용어

### 2-1. 노드

노드는 트리를 구성하고 있는 기본적인 요소로 노드와 노드가 연결되어 트리가 완성됩니다.

----

### 2-2. 간선

노드와 노드를 이어주는 선입니다.

----

### 2-3. 루트 노드

루트 노드는 트리의 최상단에 있는 노드로 루트 노드는 부모 노드가 없다는 특징이 있습니다.

----

### 2-4. 부모 노드

부모 노드는 자식 노드을 가지는 노드를 의미합니다.

----

### 2-5. 자식 노드

자식 노드는 부모 노드의 하위 노드를 의미합니다.

----

### 2-6. 단말 노드

단말 노드는 자식 노드가 없는 노드를 의미합니다.

----

## 3. 이진 트리란?

이진 트리는 각각의 노드들이 가지는 자식 노드가 2개 이하인 경우를 이진 트리라고 합니다.

----

## 4. C++에서의 이진 트리

이진 트리는 C++에서 아래와 같이 만들어서 사용할 수 있습니다.

```cpp
#include <iostream>
#include <memory>

using namespace std;

template <typename T>
class Node {
public: 
    T data;
    unique_ptr<Node> left;
    unique_ptr<Node> right;
    
    Node(T data) {
        this->data = data;
    }
};

template <typename T>
class Tree {
public:
    unique_ptr<Node<T>> root;

    void addNode(unique_ptr<Node<T>>& current, T data) {
        if (current->left == nullptr) {
            current->left = make_unique<Node<T>>(data);
            return;
        }
        if (current->right == nullptr) {
            current->right = make_unique<Node<T>>(data);
            return;
        }
        
        if (current->left != nullptr) addNode(current->left, data);
        if (current->right != nullptr) addNode(current->right, data);
    }
    
    Tree(T data) {
        this->root = make_unique<Node<T>>(data);
    }
};

int main() {
    Tree tree(3);
    
    tree.addNode(tree.root, 2);
    
    cout << tree.root->left->data;
}
```
{: file="main.cpp" }
```
2
```
{: file="output" }

트리 구조를 C++에서 구현한 모습입니다.

