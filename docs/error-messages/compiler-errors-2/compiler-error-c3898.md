---
title: 編譯器錯誤 C3898 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3898
dev_langs:
- C++
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39fe816c2637df5e5a474718d70b404bbc0c2df6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030023"
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