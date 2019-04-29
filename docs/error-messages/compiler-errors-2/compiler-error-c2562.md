---
title: 編譯器錯誤 C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: c665c4ed82fefaf0ee724defb8c205f86fc06dd0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228880"
---
# <a name="compiler-error-c2562"></a>編譯器錯誤 C2562

'identifier': 'void' 函式會傳回值

此函式宣告為`void`但傳回的值。

此錯誤可能被因不正確的函式原型。

如果您指定的傳回型別函式宣告中，可能會修正此錯誤。

下列範例會產生 C2562:

```
// C2562.cpp
// compile with: /c
void testfunc() {
   int i;
   return i;   // C2562 delete the return to resolve
}
```