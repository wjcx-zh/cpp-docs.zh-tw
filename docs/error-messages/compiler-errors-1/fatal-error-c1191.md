---
title: 嚴重錯誤 C1191
ms.date: 11/04/2016
f1_keywords:
- C1191
helpviewer_keywords:
- C1191
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
ms.openlocfilehash: 7c6756dec29138af534278742d99c2f77109b1cc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747289"
---
# <a name="fatal-error-c1191"></a>嚴重錯誤 C1191

只能在全域範圍匯入 ' dll '

將 mscorlib.dll 匯入到使用/clr 程式設計之程式的指示不能出現在命名空間或函式中，但必須出現在全域範圍中。

下列範例會產生 C1191：

```cpp
// C1191.cpp
// compile with: /clr
namespace sample {
   #using <mscorlib.dll>   // C1191 not at global scope
}
```

可能的解決方案：

```cpp
// C1191b.cpp
// compile with: /clr /c
#using <mscorlib.dll>
namespace sample {}
```
