---
title: 編譯器警告 （層級 1） C4145 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4145
dev_langs:
- C++
helpviewer_keywords:
- C4145
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65d041b9fdb7fb4b01abfadf5010444b0e406220
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100673"
---
# <a name="compiler-warning-level-1-c4145"></a>編譯器警告 (層級 1) C4145

'expression1': 關聯運算式作為 switch 運算式；可能與 '%$L' 混淆

`switch` 陳述式使用關聯運算式作為其控制運算式，因而導致 **case** 陳述式的布林值。 您是不是指 *expression2*？

## <a name="example"></a>範例

下列範例會產生 C4145：

```
// C4145.cpp
// compile with: /W1
int main() {
   int i = 0;
   switch(i == 1) {   // C4145, use i instead of i == 1 to resolve
      case 1:
         break;
      default:
         break;
   }
}
```