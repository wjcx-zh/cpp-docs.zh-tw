---
title: 編譯器錯誤 C2246
ms.date: 11/04/2016
f1_keywords:
- C2246
helpviewer_keywords:
- C2246
ms.assetid: 4f3e4f83-21f3-4256-af96-43e0bb060311
ms.openlocfilehash: c7dac0abb7d65d3f26522ea1a04577643b7b9eca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212822"
---
# <a name="compiler-error-c2246"></a>編譯器錯誤 C2246

'identifier' : 在區域定義類別中的靜態資料成員不合法

宣告具有區域範圍之類別、結構或等位的成員 **`static`** 。

下列範例會產生 C2246：

```cpp
// C2246.cpp
// compile with: /c
void func( void ) {
   class A { static int i; };   // C2246  i is local to func
   static int j;   // OK
};
```
