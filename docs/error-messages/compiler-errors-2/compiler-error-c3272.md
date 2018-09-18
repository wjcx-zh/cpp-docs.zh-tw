---
title: 編譯器錯誤 C3272 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3272
dev_langs:
- C++
helpviewer_keywords:
- C3272
ms.assetid: 7cdf254d-f207-4116-a1bf-7386f3b82a6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eaadad23d5647a0f27f4bbd9119c192f406da265
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018551"
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
