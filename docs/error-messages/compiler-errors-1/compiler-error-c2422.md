---
title: 編譯器錯誤 C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 39f779ee846cf4f328f9c7af59ae394d97d7a3ca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744728"
---
# <a name="compiler-error-c2422"></a>編譯器錯誤 C2422

' 運算元 ' 中有不合法的區段覆寫

內嵌組解碼程式碼在運算元上不正確地使用區段覆寫運算子（冒號）。  可能的原因包括：

- 運算子前面的註冊不是區段暫存器。

- 運算子前面的暫存器不是運算元中唯一的區段註冊。

- 區段覆寫運算子會出現在間接取值運算子（括弧）內。

- 在區段覆寫運算子後面的運算式不是立即運算元或記憶體運算元。

下列範例會產生 C2422：

```cpp
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```
