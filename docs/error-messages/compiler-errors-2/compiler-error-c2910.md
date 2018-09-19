---
title: 編譯器錯誤 C2910 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2910
dev_langs:
- C++
helpviewer_keywords:
- C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d726fffa61ed80352626df7a6f89467c420152bd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136123"
---
# <a name="compiler-error-c2910"></a>編譯器錯誤 C2910

'function': 無法明確特製化

編譯器偵測到嘗試明確地特製化函式兩次。

下列範例會產生 C2910:

```
// C2910.cpp
// compile with: /c
template <class T>
struct S;

template <> struct S<int> { void f() {} };
template <> void S<int>::f() {}   // C2910 delete this specialization
```

如果您嘗試明確地特製化非樣板成員，也可能會產生 C2910。 也就是說，您可以只明確特製化函式樣板。

下列範例會產生 C2910:

```
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

在 Visual Studio.NET 2003年中已完成的編譯器一致性工作，也產生這個錯誤:。

程式碼都是有效的 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中，移除`template <>`。

下列範例會產生 C2910:

```
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