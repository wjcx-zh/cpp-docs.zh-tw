---
title: 編譯器警告 （層級 1） C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: 762f52c9f051a660cce68d424e02fc45422376e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302276"
---
# <a name="compiler-warning-level-1-c4142"></a>編譯器警告 （層級 1） C4142

良性的類型重複定義

類型已重新定義已不會影響產生的程式碼的方式。

您可以檢查下列可能的原因來進行修正：

- 在衍生類別的成員函式具有不同傳回的型別對應的成員函式的基底類別。

- 使用定義的型別`typedef`命令會重新定義，使用不同的語法。

下列範例會產生 C4142:

```
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```