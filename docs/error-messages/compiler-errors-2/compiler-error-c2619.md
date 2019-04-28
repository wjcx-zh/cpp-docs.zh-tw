---
title: 編譯器錯誤 C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: f82b315a3e7ae4bb1f6d281e1d80ddc2c7fb0dea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208424"
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