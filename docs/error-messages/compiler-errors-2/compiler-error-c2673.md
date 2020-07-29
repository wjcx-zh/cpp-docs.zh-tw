---
title: 編譯器錯誤 C2673
ms.date: 11/04/2016
f1_keywords:
- C2673
helpviewer_keywords:
- C2673
ms.assetid: 780230c0-619b-4a78-b01d-ff5886306741
ms.openlocfilehash: 1a27b41c11905a509889d46da655900b69070445
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216111"
---
# <a name="compiler-error-c2673"></a>編譯器錯誤 C2673

' function '：全域函式沒有 ' this ' 指標

全域函數嘗試存取 **`this`** 。

下列範例會產生 C2673：

```cpp
// C2673.cpp
int main() {
   this = 0;   // C2673
}
```
