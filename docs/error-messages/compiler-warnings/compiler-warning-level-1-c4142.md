---
title: 編譯器警告（層級1） C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: 3c9ab9c22d41e7732c86d43f5c6b4f09c50bbda8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87196847"
---
# <a name="compiler-warning-level-1-c4142"></a>編譯器警告（層級1） C4142

類型的良性重新定義

類型會以對產生的程式碼沒有任何影響的方式重新定義。

您可以檢查下列可能的原因來進行修正：

- 衍生類別的成員函式具有不同于基類之對應成員函式的傳回型別。

- 以命令定義的類型 **`typedef`** 會使用不同的語法重新定義。

下列範例會產生 C4142：

```c
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```
