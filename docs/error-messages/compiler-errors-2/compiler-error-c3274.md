---
title: 編譯器錯誤 C3274
ms.date: 11/04/2016
f1_keywords:
- C3274
helpviewer_keywords:
- C3274
ms.assetid: 1f03f18e-b569-48eb-9249-11c70122a305
ms.openlocfilehash: d28deea0729a091ce0829187323a0d5a2d184944
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753818"
---
# <a name="compiler-error-c3274"></a>編譯器錯誤 C3274

__finally/finally 缺少對應的 try

找到缺少對應之 [的](../../cpp/try-finally-statement.md) __finally [或](../../dotnet/finally.md) finally `try`陳述式。 若要解決這個問題，請刪除 `__finally` 陳述式，或為 `try` 加入 `__finally`陳述式。

下列範例會產生 C3274：

```cpp
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
