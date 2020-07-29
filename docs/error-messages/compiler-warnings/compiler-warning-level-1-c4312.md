---
title: 編譯器警告 (層級 1) C4312
ms.date: 11/04/2016
f1_keywords:
- C4312
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
ms.openlocfilehash: 379803260492449da4985e62d36750f121b4e7fa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233258"
---
# <a name="compiler-warning-level-1-c4312"></a>編譯器警告 (層級 1) C4312

'operation' : 將 'type1' 轉換為較大的 'type2'

此警告會偵測到將32位值指派給64位指標類型的嘗試，例如，將32位 **`int`** 或轉換 **`long`** 成64位指標。

這可能是不安全的轉換，即使在發生正負號擴充時納入 32 位元指標值也是如此。 負的 32 位元整數指派給 64 位元指標類型，正負號擴充會使指標值參考不同於整數值的記憶體位址。

只會針對 64 位元編譯目標發出這個警告。 如需詳細資訊，請參閱[使用指標的規則](/windows/win32/WinProg64/rules-for-using-pointers)。

為 64 位元目標編譯時，下列程式碼範例會產生 C4312：

```cpp
// C4312.cpp
// compile by using: cl /W1 /LD C4312.cpp
void* f(int i) {
   return (void*)i;   // C4312 for 64-bit targets
}

void* f2(__int64 i) {
   return (void*)i;   // OK
}
```
