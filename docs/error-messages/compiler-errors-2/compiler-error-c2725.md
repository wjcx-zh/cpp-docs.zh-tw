---
title: 編譯器錯誤 C2725
ms.date: 11/04/2016
f1_keywords:
- C2725
helpviewer_keywords:
- C2725
ms.assetid: 13cd5b1b-e906-4cd8-9b2b-510d587c665a
ms.openlocfilehash: 5df5a94e32e3cb365166fc38c5df10c248138277
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756403"
---
# <a name="compiler-error-c2725"></a>編譯器錯誤 C2725

'exception'：無法以值或參考擲回或攔截 managed 或 WinRT 物件

managed 或 WinRT 例外狀況的類型不正確。

## <a name="example"></a>範例

下列範例會產生 C2725，並顯示如何修正此問題。

```cpp
// C2725.cpp
// compile with: /clr
ref class R {
public:
   int i;
};

int main() {
   R % r1 = *gcnew R;
   throw r1;   // C2725

   R ^ r2 = gcnew R;
   throw r2;   // OK
}
```

## <a name="example"></a>範例

下列範例會產生 C2725，並顯示如何修正此問題。

```cpp
// C2725b.cpp
// compile with: /clr
using namespace System;
int main() {
   try {}
   catch( System::Exception%) {}   // C2725
   // try the following line instead
   // catch( System::Exception ^e) {}
}
```
