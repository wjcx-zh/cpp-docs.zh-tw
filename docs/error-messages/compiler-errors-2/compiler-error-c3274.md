---
title: 編譯器錯誤 C3274
ms.date: 11/04/2016
f1_keywords:
- C3274
helpviewer_keywords:
- C3274
ms.assetid: 1f03f18e-b569-48eb-9249-11c70122a305
ms.openlocfilehash: a44a7d471e7e079ee43afa8bf58fd590be2f4bf8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506661"
---
# <a name="compiler-error-c3274"></a>編譯器錯誤 C3274

__finally/finally 缺少對應的 try

找到缺少對應之 [的](../../cpp/try-finally-statement.md) __finally [或](../../dotnet/finally.md) finally `try`陳述式。 若要解決這個問題，請刪除 `__finally` 陳述式，或為 `try` 加入 `__finally`陳述式。

下列範例會產生 C3274：

```
// C3274.cpp
// compile with: /clr
// C3274 expected
using namespace System;
int main() {
   try {
      try {
         throw gcnew ApplicationException();
      }
      catch(...) {
         Console::Error->WriteLine(L"Caught an exception");
      }
      finally {
         Console::WriteLine(L"In finally");
      }
   } finally {
      Console::WriteLine(L"In finally");
   }

   // Uncomment the following 3 lines to resolve.
   // try {
   //   throw gcnew ApplicationException();
   // }

   finally {
      Console::WriteLine(L"In finally");
   }
   Console::WriteLine(L"**FAIL**");
}
```