---
title: 編譯器錯誤 C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: f82b315a3e7ae4bb1f6d281e1d80ddc2c7fb0dea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662908"
---
# <a name="compiler-error-c2619"></a>編譯器錯誤 C2619

'identifier'：匿名結構/等位不能有靜態資料成員

匿名結構或等位的成員會宣告成 `static`。

下列範例會產生 C2619，並示範如何修正藉由移除 static 關鍵字修正此問題。

```
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```