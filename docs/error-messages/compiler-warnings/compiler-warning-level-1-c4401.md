---
title: 編譯器警告（層級1） C4401
ms.date: 11/04/2016
f1_keywords:
- C4401
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
ms.openlocfilehash: 242c854339608c88d139c898d81d142c52f90134
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966307"
---
# <a name="compiler-warning-level-1-c4401"></a>編譯器警告（層級1） C4401

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