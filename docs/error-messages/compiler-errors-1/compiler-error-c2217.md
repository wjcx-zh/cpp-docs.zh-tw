---
title: 編譯器錯誤 C2217
ms.date: 11/04/2016
f1_keywords:
- C2217
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
ms.openlocfilehash: b033d95b127a45451a776cdc336ea7d2649d3716
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87209743"
---
# <a name="compiler-error-c2217"></a>編譯器錯誤 C2217

' attribute1 ' 需要 ' attribute2 '

第一個函式屬性需要第二個屬性。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 中斷（ `__interrupt` ）函數宣告為 `near` 。 中斷功能必須是 `far` 。

1. 使用、或宣告的中斷函式 **`__stdcall`** **`__fastcall`** 。 中斷功能必須使用 C 呼叫慣例。

## <a name="example"></a>範例

如果您嘗試將委派系結至接受可變引數數目的 CLR 函式，也可能會發生 C2217。 如果函數也有 e param 陣列多載，請改為使用它。 下列範例會產生 C2217。

```cpp
// C2217.cpp
// compile with: /clr
using namespace System;
delegate void MyDel(String^, Object^, Object^, ...);   // C2217
delegate void MyDel2(String ^, array<Object ^> ^);   // OK

int main() {
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);
   array<Object ^ > ^ x = gcnew array<Object ^>(2);
   x[0] = safe_cast<Object^>(0);
   x[1] = safe_cast<Object^>(1);

   // wl("{0}, {1}", 0, 1);
   wl("{0}, {1}", x);
}
```
