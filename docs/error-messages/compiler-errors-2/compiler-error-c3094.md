---
title: 編譯器錯誤 C3094
ms.date: 11/04/2016
f1_keywords:
- C3094
helpviewer_keywords:
- C3094
ms.assetid: 10da9b7c-e72d-4013-9925-c83e1bb142db
ms.openlocfilehash: 1b2cd29738763e5b31cc6727126114fca509a47f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512562"
---
# <a name="compiler-error-c3094"></a>編譯器錯誤 C3094

'attribute': 不允許匿名使用

未正確設定屬性的範圍。  如需詳細資訊，請參閱 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3094。

```
// C3094.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
public ref class AAttribute : Attribute {};

[A];   // C3094

// OK
[A]
ref class x{};
```