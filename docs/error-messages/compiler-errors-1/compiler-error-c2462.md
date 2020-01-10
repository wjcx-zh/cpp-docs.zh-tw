---
title: 編譯器錯誤 C2462
ms.date: 11/04/2016
f1_keywords:
- C2462
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
ms.openlocfilehash: 4eb50ddac51ea78ab3a28d7703384f02eb026ecb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743922"
---
# <a name="compiler-error-c2462"></a>編譯器錯誤 C2462

' identifier '：無法定義 ' new-運算式 ' 中的類型

您不能在 `new` 運算子的 [運算元] 欄位中定義型別。 將類型定義放在個別的語句中。

下列範例會產生 C2462：

```cpp
// C2462.cpp
int main() {
   new struct S { int i; };   // C2462
}
```
