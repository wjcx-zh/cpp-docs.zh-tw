---
title: 編譯器錯誤 C2502
ms.date: 11/04/2016
f1_keywords:
- C2502
helpviewer_keywords:
- C2502
ms.assetid: affa0b86-15fc-4e17-b7f2-6aad4a3771c4
ms.openlocfilehash: bb0e9cc16d403439dc74ae7c93cfe51e370b199a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218204"
---
# <a name="compiler-error-c2502"></a>編譯器錯誤 C2502

' identifier '：基類上有太多的存取修飾詞

基類有一個以上的存取修飾詞。 只允許一個存取修飾詞（ **`public`** 、 **`private`** 或 **`protected`** ）。

下列範例會產生 C2502：

```cpp
// C2502.cpp
// compile with: /c
class A { };
class B { };
class C : private public A { };   // C2502

// OK
class D : private A {};
class E : public A, private B {};
```
