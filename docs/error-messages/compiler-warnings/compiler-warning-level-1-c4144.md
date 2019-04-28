---
title: 編譯器警告 （層級 1） C4144
ms.date: 11/04/2016
f1_keywords:
- C4144
helpviewer_keywords:
- C4144
ms.assetid: a37b445d-dbc6-43b4-8d95-ffd0e4225464
ms.openlocfilehash: b2406357baf70e45566f2d2f25839d151bac4186
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352945"
---
# <a name="compiler-warning-level-1-c4144"></a>編譯器警告 （層級 1） C4144

'expression': 關聯運算式做為 switch 運算式

指定的關聯運算式所做的控制運算式[切換](../../cpp/switch-statement-cpp.md)陳述式。 布林值，將提供相關聯的 case 陳述式。 下列範例會產生 C4144:

```
// C4144.cpp
// compile with: /W1
int main()
{
   int i = 0;
   switch(!i) {   // C4144, remove the ! to resolve
      case 1:
         break;
      default:
         break;
   }
}
```