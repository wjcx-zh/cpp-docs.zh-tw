---
title: 編譯器錯誤 C2246
ms.date: 11/04/2016
f1_keywords:
- C2246
helpviewer_keywords:
- C2246
ms.assetid: 4f3e4f83-21f3-4256-af96-43e0bb060311
ms.openlocfilehash: 89352029afbae4d977a4109f76c0e18bb761b4d4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758914"
---
# <a name="compiler-error-c2246"></a>編譯器錯誤 C2246

'identifier' : 在區域定義類別中的靜態資料成員不合法

具有本機領域的類別、結構或等位的成員宣告為 `static`。

下列範例會產生 C2246：

```cpp
// C2246.cpp
// compile with: /c
void func( void ) {
   class A { static int i; };   // C2246  i is local to func
   static int j;   // OK
};
```
