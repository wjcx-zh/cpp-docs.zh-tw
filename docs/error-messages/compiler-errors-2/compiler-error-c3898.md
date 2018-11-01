---
title: 編譯器錯誤 C3898
ms.date: 11/04/2016
f1_keywords:
- C3898
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
ms.openlocfilehash: 503f295d62c598e3138b1a001d6b350c0d90ea84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549730"
---
# <a name="compiler-error-c3898"></a>編譯器錯誤 C3898

'var': 類型的資料成員只能是受控類型的成員

[Initonly](../../dotnet/initonly-cpp-cli.md)原生類別中宣告資料成員。  `initonly`資料成員只能在 CLR 類別中宣告。

下列範例會產生 C3898:

```
// C3898.cpp
// compile with: /clr
struct Y1 {
   initonly
   static int data_var = 9;   // C3898
};
```

可能的解決方式：

```
// C3898b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int data_var = 9;
};
```