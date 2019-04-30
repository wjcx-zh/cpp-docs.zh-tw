---
title: 編譯器警告 (層級 1) C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: af091d1d35fff955afcc5af3da48b80416e79f36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385429"
---
# <a name="compiler-warning-level-1-c4731"></a>編譯器警告 (層級 1) C4731

'pointer': 框架指標暫存器的 「 註冊 」 修改內嵌組譯碼

已修改框架指標暫存器。 您必須儲存並還原暫存器，在您內嵌組件區塊或框架的變數 （區域變數或參數，根據修改的暫存器），或您的程式碼可能無法正常運作。

下列範例會產生 C4731:

```
// C4731.cpp
// compile with: /W1 /LD
// processor: x86
// C4731 expected
void bad(int p) {
   __asm
   {
      mov ebp, 1
   }

   if (p == 1)
   {
      // ...
   }
}
```

EBP （FPO 不允許） 框架指標，而且正在修改。 當`p`稍後參考，它參考相對於`EBP`。 但`EBP`已被覆寫的程式碼，因此程式將無法正常運作，甚至可能會發生錯誤。