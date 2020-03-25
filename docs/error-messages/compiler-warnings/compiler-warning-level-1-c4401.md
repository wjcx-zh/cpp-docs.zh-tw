---
title: 編譯器警告 (層級 1) C4401
ms.date: 11/04/2016
f1_keywords:
- C4401
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
ms.openlocfilehash: fe08509a05eed00f7e7d492e723e873d05e451ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162656"
---
# <a name="compiler-warning-level-1-c4401"></a>編譯器警告 (層級 1) C4401

' bit '：成員是位欄位

內嵌組解碼程式碼嘗試存取位欄位成員。 內嵌組解碼無法存取位欄位成員，因此使用位欄位成員之前的最後一個封裝界限。

若要避免這個警告，請先將位欄位轉換成適當的類型，然後再于內嵌組解碼程式碼中進行參考。 下列範例會產生 C4401：

```cpp
// C4401.cpp
// compile with: /W1
// processor: x86
typedef struct bitfield {
   signed bit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bf.bit = 0;
   __asm {
      mov bf.bit,0;   // C4401
   }

   /* use the following __asm block to resolve the warning
   int i = (int)bf.bit;
   __asm {
      mov i,0;
   }
   */
}
```
