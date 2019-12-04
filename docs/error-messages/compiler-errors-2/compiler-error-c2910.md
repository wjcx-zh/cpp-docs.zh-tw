---
title: 編譯器錯誤 C2910
ms.date: 11/04/2016
f1_keywords:
- C2910
helpviewer_keywords:
- C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
ms.openlocfilehash: 0061a7171dd08440ec5d8c8b8cadb77303ff8f41
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761111"
---
# <a name="compiler-error-c2910"></a>編譯器錯誤 C2910

' function '：無法明確特製化

編譯器偵測到嘗試明確特殊化函數兩次。

下列範例會產生 C2910：

```cpp
// C2910.cpp
// compile with: /c
template <class T>
struct S;

template <> struct S<int> { void f() {} };
template <> void S<int>::f() {}   // C2910 delete this specialization
```

如果您嘗試明確特殊化非範本成員，也可以產生 C2910。 也就是說，您只能明確特殊化函式樣板。

下列範例會產生 C2910：

```cpp
// C2910b.cpp
// compile with: /c
template <class T> struct A {
   A(T* p);
};

template <> struct A<void> {
   A(void* p);
};

template <class T>
inline A<T>::A(T* p) {}

template <> A<void>::A(void* p){}   // C2910
// try the following line instead
// A<void>::A(void* p){}
```

在 Visual Studio .NET 2003：中完成的編譯器一致性工作也會產生此錯誤。

若要讓程式碼在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C++中都有效，請移除 `template <>`。

下列範例會產生 C2910：

```cpp
// C2910c.cpp
// compile with: /c
template <class T> class A {
   void f();
};

template <> class A<int> {
   void f();
};

template <> void A<int>::f() {}   // C2910
// try the following line instead
// void A<int>::f(){}   // OK
```
