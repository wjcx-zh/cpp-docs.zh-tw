---
title: 編譯器錯誤 C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: b64eccac351c6bdd8ac388278a6e264cc7a84868
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220297"
---
# <a name="compiler-error-c2619"></a>編譯器錯誤 C2619

'identifier'：匿名結構/等位不能有靜態資料成員

宣告匿名結構或等位的成員 **`static`** 。

下列範例會產生 C2619，並示範如何修正藉由移除 static 關鍵字修正此問題。

```cpp
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```
