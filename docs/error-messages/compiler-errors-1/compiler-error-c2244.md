---
title: 編譯器錯誤 C2244
ms.date: 11/04/2016
f1_keywords:
- C2244
helpviewer_keywords:
- C2244
ms.assetid: d9911c12-ceb5-4f93-ac47-b44a485215c2
ms.openlocfilehash: 97ff469c6f3f766bd1b5412133003bae2acaddfc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759473"
---
# <a name="compiler-error-c2244"></a>編譯器錯誤 C2244

' identifier '：無法將函式定義與現有的宣告比對

一元 + 運算子不尋常的用法，用於沒有括弧的函式呼叫前面。

這個錯誤只會發生C++在專案中。

下列範例會產生 C2244：

```cpp
// C2244.cpp
int func(char) {
   return 0;
}

int func(int) {
   return 0;
}

int main() {
   +func;   // C2244
}
```

當類別樣板的成員函式使用了不正確的函數簽章時，也可能會發生 C2244。

```cpp
// C2244b.cpp
// compile with: /c
template<class T>
class XYZ {
   void func(T t);
};

template<class T>
void XYZ<T>::func(int i) {}   // C2244 wrong function signature
// try the following line instead
// void XYZ<T>::func(T t) {}
```

當成員函式樣板使用了不正確的函數簽章時，也可能會發生 C2244。

```cpp
// C2244c.cpp
// compile with: /c
class ABC {
   template<class T>
   void func(int i, T t);
};

template<class T>
void ABC::func(int i) {}   // C2244 wrong signature
// try the following line instead
// void ABC::func(int i, T t) {}
```

您不能部分特殊化函式樣板。

```cpp
// C2244d.cpp
template<class T, class U>
class QRS {
   void func(T t, U u);
};

template<class T>
void QRS<T,int>::func(T t, int u) {}   // C2244
```
