---
title: 編譯器錯誤 C3898
ms.date: 11/04/2016
f1_keywords:
- C3898
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
ms.openlocfilehash: 02c649fb906b0c5f09afe25952a8670c1a0e7f3d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749200"
---
# <a name="compiler-error-c3898"></a>編譯器錯誤 C3898

' var '：類型資料成員只能是 managed 類型的成員

在原生類別中宣告了[initonly](../../dotnet/initonly-cpp-cli.md)資料成員。  `initonly` 的資料成員只能在 CLR 類別中宣告。

下列範例會產生 C3898：

```cpp
// C3898.cpp
// compile with: /clr
struct Y1 {
   initonly
   static int data_var = 9;   // C3898
};
```

可能的解決方案：

```cpp
// C3898b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int data_var = 9;
};
```
