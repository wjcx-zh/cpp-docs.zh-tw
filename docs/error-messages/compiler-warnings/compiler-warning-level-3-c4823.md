---
title: 編譯器警告 (層級 3) C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: 28d490c341c4d14c2e6c03e13007b5a8be423622
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625899"
---
# <a name="compiler-warning-level-3-c4823"></a>編譯器警告 (層級 3) C4823

'function': 使用 pin 指標但回溯語意不會啟用。 請考慮使用 /EHa

若要取消釘選在 managed 堆積在區塊範圍中宣告 pin 指標所指向的物件，編譯器會模擬 「 假裝 」 的釘選的指標含有 nullifies 指標解構函式的本機類別的解構函式的行為。 若要啟用解構函式呼叫之後擲回例外狀況，您必須啟用物件回溯，您可以使用來這麼做[/EHsc](../../build/reference/eh-exception-handling-model.md)。

也以手動方式，您可以取消釘選的物件，並忽略此警告。

## <a name="example"></a>範例

下列範例會產生 C4823。

```
// C4823.cpp
// compile with: /clr /W3 /EHa-
using namespace System;

ref struct G {
   int m;
};

void f(G ^ pG) {
   try {
      pin_ptr<int> p = &pG->m;
      // manually unpin, ignore warning
      // p = nullptr;
      throw gcnew Exception;
   }
   catch(Exception ^) {}
}   // C4823 warning

int main() {
   f( gcnew G );
}
```
