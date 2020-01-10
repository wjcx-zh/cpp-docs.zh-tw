---
title: 編譯器警告 (層級 3) C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: a96877252b0b7699f5e4033f8e695f4d9016a6c9
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541271"
---
# <a name="compiler-warning-level-3-c4823"></a>編譯器警告 (層級 3) C4823

' function '：使用釘選指標，但是未啟用回溯語義。 考慮使用/EHa

若要在區塊範圍中所宣告的釘選指標上取消釘選 managed 堆積上的物件，編譯器會模擬本機類別的析構函數行為，「偽裝」釘選指標具有 nullifies 指標的析構函式。 若要在擲回例外狀況之後啟用對函式的呼叫，您必須啟用物件回溯，您可以使用[/ehsc](../../build/reference/eh-exception-handling-model.md)來執行此動作。

您也可以手動取消釘選物件，並忽略警告。

## <a name="example"></a>範例

下列範例會產生 C4823。

```cpp
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
