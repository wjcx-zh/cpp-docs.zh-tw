---
title: 編譯器錯誤 C3842
ms.date: 11/04/2016
f1_keywords:
- C3842
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
ms.openlocfilehash: a61a69aca53f7f8996d0261a57b749930ecc01cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638343"
---
# <a name="compiler-error-c3842"></a>編譯器錯誤 C3842

'function'：不支援 WinRT 或 Managed 類型的成員函式上的 'const' 和 'volatile' 限定詞

[const](../../cpp/const-cpp.md)並[volatile](../../cpp/volatile-cpp.md)不支援的 Windows 執行階段或 managed 的類型的成員函式。

下列範例會產生 C3842：

```
// C3842a.cpp
// compile with: /clr /c
public ref struct A {
   void f() const {}   // C3842
   void f() volatile {}   // C3842

   void f() {}
};
```