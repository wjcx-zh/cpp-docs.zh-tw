---
title: 編譯器錯誤 C2462
ms.date: 11/04/2016
f1_keywords:
- C2462
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
ms.openlocfilehash: 8db79bf9813d9701b45d9a0427f68cfbecc3eba4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214668"
---
# <a name="compiler-error-c2462"></a>編譯器錯誤 C2462

' identifier '：無法定義 ' new-運算式 ' 中的類型

您無法在運算子的 [運算元] 欄位中定義型別 **`new`** 。 將類型定義放在個別的語句中。

下列範例會產生 C2462：

```cpp
// C2462.cpp
int main() {
   new struct S { int i; };   // C2462
}
```
