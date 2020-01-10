---
title: 編譯器錯誤 C2765
ms.date: 11/04/2016
f1_keywords:
- C2765
helpviewer_keywords:
- C2765
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
ms.openlocfilehash: 0c646d0ab28b97b546721180e46b0f22ea376f7d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759824"
---
# <a name="compiler-error-c2765"></a>編譯器錯誤 C2765

' function '：函式樣板的明確特製化不能有任何預設引數

函式樣板的明確特製化不允許預設引數。 如需詳細資訊，請參閱函式樣板[的明確特製化](../../cpp/explicit-specialization-of-function-templates.md)。

下列範例會產生 C2765：

```cpp
// C2765.cpp
template<class T> void f(T t) {};

template<> void f<char>(char c = 'a') {}   // C2765
// try the following line instead
// template<> void f<char>(char c) {}
```
