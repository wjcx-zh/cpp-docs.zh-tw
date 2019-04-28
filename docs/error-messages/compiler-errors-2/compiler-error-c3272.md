---
title: 編譯器錯誤 C3272
ms.date: 11/04/2016
f1_keywords:
- C3272
helpviewer_keywords:
- C3272
ms.assetid: 7cdf254d-f207-4116-a1bf-7386f3b82a6f
ms.openlocfilehash: 3e4348dcce0cfd04234b515877d788e5330f8e4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365685"
---
# <a name="compiler-error-c3272"></a>編譯器錯誤 C3272

'symbol' : 符號必須有 FieldOffset，因為它是用 StructLayout(LayoutKind::Explicit) 定義的類型 typename 的成員

當 `StructLayout(LayoutKind::Explicit)` 生效時，欄位必須標記為 `FieldOffset`。

下列範例會產生 C3272：

```
// C3272_2.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Explicit)]
ref struct X
{
   int data_;   // C3272
   // try the following line instead
   // [FieldOffset(0)] int data_;
};
```
