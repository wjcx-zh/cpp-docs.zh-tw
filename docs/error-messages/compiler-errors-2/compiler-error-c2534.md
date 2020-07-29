---
title: 編譯器錯誤 C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: 202e3bbe2238b4cc2a5233ac4e093717d623f099
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207897"
---
# <a name="compiler-error-c2534"></a>編譯器錯誤 C2534

' identifier '：函式無法傳回值

函式無法傳回值或具有傳回類型（甚至是傳回 **`void`** 類型）。

從函式定義中移除語句，即可修正此錯誤 **`return`** 。

下列範例會產生 C2534：

```cpp
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```
