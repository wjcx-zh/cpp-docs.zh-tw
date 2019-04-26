---
title: 編譯器錯誤 C3226
ms.date: 11/04/2016
f1_keywords:
- C3226
helpviewer_keywords:
- C3226
ms.assetid: 636106ca-6f4e-4303-a6a0-8803221ec67d
ms.openlocfilehash: 39b715b580d6fca9c15e5b9e2b63a9afb609eb16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173999"
---
# <a name="compiler-error-c3226"></a>編譯器錯誤 C3226

泛型宣告內不允許有樣板宣告，必須改為泛型宣告

請在泛型類別內使用泛型宣告。

下列範例會產生 C3226：

```
// C3226.cpp
// compile with: /clr
generic <class T>
ref class C {
   template <class T1>   // C3226
   ref struct S1 {};
};
```

下列範例示範可能的解決方式：

```
// C3226b.cpp
// compile with: /clr /c
generic <class T>
ref class C {
   generic <class T1>
   ref struct S1 {};
};
```