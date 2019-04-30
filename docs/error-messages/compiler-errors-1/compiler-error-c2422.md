---
title: 編譯器錯誤 C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 524eeadb6cf066d3eba3a7e88c45a9e2b993c0ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402878"
---
# <a name="compiler-error-c2422"></a>編譯器錯誤 C2422

'運算元' 中的不合法的區段覆寫

內嵌組譯碼不正確地使用一個運算元的區段覆寫運算子 （冒號）。  可能的原因包括：

- 運算子之前的暫存器不是區段暫存器。

- 運算子之前的暫存器不是唯一的區段暫存器中，運算元中。

- 區段覆寫運算子會出現在間接取值運算子 （括號）。

- 下列區段覆寫運算子的運算式不是即時的運算元或記憶體運算元。

下列範例會產生 C2422:

```
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```