---
title: 編譯器錯誤 C2217
ms.date: 11/04/2016
f1_keywords:
- C2217
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
ms.openlocfilehash: f178f969afa189910c9d23d70226ecc6c15876a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353532"
---
# <a name="compiler-error-c2217"></a>編譯器錯誤 C2217

'attribute1' 需要 'attribute2'

第一個函式屬性需要第二個屬性。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 插斷 (`__interrupt`) 函式宣告為`near`。 中斷函式必須是`far`。

1. 中斷與宣告的函式`__stdcall`，或`__fastcall`。 中斷函式必須使用 C 呼叫慣例。

## <a name="example"></a>範例

如果您嘗試將委派繫結至接受可變數目的引數的 CLR 函式，也會發生 C2217。 如果函式也會有電子 param 陣列的多載，請改為可使用。 下列範例會產生 C2217。

```
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