---
title: 編譯器錯誤 C2093
ms.date: 11/04/2016
f1_keywords:
- C2093
helpviewer_keywords:
- C2093
ms.assetid: 17529a70-9169-46b5-9fc6-57a5ce224e6a
ms.openlocfilehash: d57b452e63f7bf76051ef6a23c5f8f6ba81aed1e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741146"
---
# <a name="compiler-error-c2093"></a>編譯器錯誤 C2093

' variable1 '：無法使用自動變數 ' variable2 ' 的位址初始化

使用[/za](../../build/reference/za-ze-disable-language-extensions.md)進行編譯時，程式會嘗試使用自動變數的位址當做初始化運算式。

下列範例會產生 C2093：

```
// C2093.c
// compile with: /Za /c
void func() {
   int li;   // an implicit auto variable
   int * s[]= { &li };   // C2093 address is not a constant

   // OK
   static int li2;
   int * s2[]= { &li2 };
}
```