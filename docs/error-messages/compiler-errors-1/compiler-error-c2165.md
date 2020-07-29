---
title: 編譯器錯誤 C2165
ms.date: 11/04/2016
f1_keywords:
- C2165
helpviewer_keywords:
- C2165
ms.assetid: b108313b-b8cb-4dce-b2ec-f2b31c9cdc87
ms.openlocfilehash: 29637dd9cb2b1faab537a970df9ef3d76fc26e0c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216345"
---
# <a name="compiler-error-c2165"></a>編譯器錯誤 C2165

'keyword': 無法修飾指向資料的指標

**`__stdcall`**、 **`__cdecl`** 或 **`__fastcall`** 關鍵字會嘗試修改資料的指標。

下列範例會產生 C2165：

```cpp
// C2165.cpp
// compile with: /c
char __cdecl *p;   // C2165
char *p;   // OK
```
