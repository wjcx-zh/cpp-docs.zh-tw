---
title: 編譯器錯誤 C2734
ms.date: 11/04/2016
f1_keywords:
- C2734
helpviewer_keywords:
- C2734
ms.assetid: e53a77b7-825c-42d1-a655-90e1c93b833e
ms.openlocfilehash: b4952f4705ad94133000fe6d84117cb04a5aa850
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206818"
---
# <a name="compiler-error-c2734"></a>編譯器錯誤 C2734

' identifier '：必須初始化 const 物件（如果不是 extern）

識別碼已宣告， **`const`** 但未初始化或 **`extern`** 。

下列範例會產生 C2734：

```cpp
// C2734.cpp
const int j;   // C2734
extern const int i;   // OK, declared as extern
```
