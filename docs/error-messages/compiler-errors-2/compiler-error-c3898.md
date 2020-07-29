---
title: 編譯器錯誤 C3898
ms.date: 11/04/2016
f1_keywords:
- C3898
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
ms.openlocfilehash: e7d1ce25e13e1b601c4abc85e71db484f7b3f822
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221025"
---
# <a name="compiler-error-c3898"></a>編譯器錯誤 C3898

' var '：類型資料成員只能是 managed 類型的成員

在原生類別中宣告了[initonly](../../dotnet/initonly-cpp-cli.md)資料成員。  **`initonly`** 資料成員只能在 CLR 類別中宣告。

下列範例會產生 C3898：

```cpp
// C3898.cpp
// compile with: /clr
struct Y1 {
   initonly
   static int data_var = 9;   // C3898
};
```

可能的解決方式：

```cpp
// C3898b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int data_var = 9;
};
```
