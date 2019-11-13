---
title: 編譯器警告（層級1） C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: b2591756dfaa8887affbe4e470f1c98738b6b680
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052420"
---
# <a name="compiler-warning-level-1-c4731"></a>編譯器警告（層級1） C4731

' 指標 '：內嵌組解碼程式碼修改了框架指標暫存器 ' register '

已修改框架指標暫存器。 您必須在內嵌組解碼區塊或框架變數（本機或參數，視已修改的暫存器）中儲存和還原暫存器，否則您的程式碼可能無法正常運作。

下列範例會產生 C4731：

```cpp
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

EBP 是框架指標（不允許 FPO），而且正在進行修改。 當稍後參考 `p` 時，就會參考相對於 `EBP`的。 但是 `EBP` 已被程式碼覆寫，因此程式將無法正常運作，甚至可能發生錯誤。