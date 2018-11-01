---
title: 編譯器錯誤 C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: d524c49075c400caa345dd26ed681734ea0cfb94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582646"
---
# <a name="compiler-error-c3642"></a>編譯器錯誤 C3642

' return_type/args ': 無法以 __clrcall 呼叫慣例，原生程式碼呼叫的函式

標記為函式[__clrcall](../../cpp/clrcall.md)無法呼叫原生 (unmanaged) 程式碼的呼叫慣例。

*return_type/引數*是函式的名稱，或是類型`__clrcall`您嘗試呼叫的函式。  您透過函式指標呼叫時，會使用型別。

若要從原生的內容中呼叫 managed 函式，您可以新增的 「 包裝函式 」 函式會呼叫`__clrcall`函式。 或者，您可以使用 CLR 封送處理機制;請參閱[如何： 封送處理函式指標使用 PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)如需詳細資訊。

下列範例會產生 C3642:

```
// C3642.cpp
// compile with: /clr
using namespace System;
struct S {
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall
      Console::WriteLine(s);
   }
   void Test2(char * s) {
      Test(gcnew String(s));
   }
};

#pragma unmanaged
int main() {
   S s;
   s.Test("abc");   // C3642
   s.Test2("abc");   // OK
}
```