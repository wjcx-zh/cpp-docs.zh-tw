---
title: 編譯器警告 (層級 1) C4401
ms.date: 11/04/2016
f1_keywords:
- C4401
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
ms.openlocfilehash: c7e6cf8a52288d895b74481678dc91fee387a6a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455415"
---
# <a name="compiler-warning-level-1-c4401"></a>編譯器警告 (層級 1) C4401

'位元欄位': 成員是位元欄位

內嵌組譯程式碼會嘗試存取的位元欄位成員。 內嵌組譯碼無法存取位元欄位成員，所以會使用位元欄位成員之前的最後一個封裝界限。

若要避免這個警告，請在內嵌組譯碼中進行參考之前，先轉換位元欄位，以適當的型別。 下列範例會產生 C4401:

```
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