---
title: 編譯器錯誤 C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: 7c3f9f05bf04c9a1c20fff7910836e7b50468a8e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742453"
---
# <a name="compiler-error-c3642"></a>編譯器錯誤 C3642

' return_type/args '：無法從機器碼呼叫具有 __clrcall 呼叫慣例的函式

以[__clrcall](../../cpp/clrcall.md)呼叫慣例標記的函式，無法從原生（非受控）程式碼呼叫。

*return_type/args*是函式的名稱，或是您嘗試呼叫之 `__clrcall` 函式的類型。  當您透過函式指標呼叫時，會使用類型。

若要從原生內容呼叫 managed 函式，您可以加入將呼叫 `__clrcall` 函式的「包裝函式」函式。 或者，您可以使用 CLR 封送處理機制;如需詳細資訊，請參閱[如何：使用 PInvoke 封送](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)處理函式指標。

下列範例會產生 C3642：

```cpp
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
