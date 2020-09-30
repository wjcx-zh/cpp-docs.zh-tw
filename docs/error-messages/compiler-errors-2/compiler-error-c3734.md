---
title: 編譯器錯誤 C3734
ms.date: 11/04/2016
f1_keywords:
- C3734
helpviewer_keywords:
- C3734
ms.assetid: 4e2afdcc-7da9-45a1-9c96-85f25e2986e8
ms.openlocfilehash: 0d49eae823eb64f97e7276d432e161b3de21d725
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510079"
---
# <a name="compiler-error-c3734"></a>編譯器錯誤 C3734

'class'：Managed 或 WinRT 類別不能是 coclass

[Coclass](../../windows/attributes/coclass.md)屬性不能與 Managed 或 WinRT 類別一起使用。

下列範例會產生 C3734，並示範如何修正此問題：

```cpp
// C3734.cpp
// compile with: /clr /c
[module(name="x")];

[coclass]
ref class CMyClass {   // C3734 remove the ref keyword to resolve
};
```
