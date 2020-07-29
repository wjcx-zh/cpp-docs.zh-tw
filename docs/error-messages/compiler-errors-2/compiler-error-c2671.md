---
title: 編譯器錯誤 C2671
ms.date: 11/04/2016
f1_keywords:
- C2671
helpviewer_keywords:
- C2671
ms.assetid: fc0ee40f-c8f3-408f-b89d-745d149c4169
ms.openlocfilehash: 795c3413699a2af0ae587980a658baa2bbcdd887
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216124"
---
# <a name="compiler-error-c2671"></a>編譯器錯誤 C2671

' function '：靜態成員函式沒有 ' this ' 指標

成員函式 **`static`** 嘗試存取 **`this`** 。

下列範例會產生 C2671：

```cpp
// C2671.cpp
struct S {
   static S* const func() { return this; }  // C2671
};
```
