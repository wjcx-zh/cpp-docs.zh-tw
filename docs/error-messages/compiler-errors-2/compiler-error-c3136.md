---
title: 編譯器錯誤 C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: 75862f3b80d617b607a7b3e735cb3e16e9a40bb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757380"
---
# <a name="compiler-error-c3136"></a>編譯器錯誤 C3136

' interface '： COM 介面只能繼承自另一個 COM 介面，' interface ' 不是 COM 介面

您套用[介面屬性](../../windows/attributes/interface-attributes.md)的介面繼承自不是 COM 介面的介面。 COM 介面最終會繼承自 `IUnknown`。 任何前面加上介面屬性的介面都是 COM 介面。

下列範例會產生 C3136：

```cpp
// C3136.cpp
#include "unknwn.h"

__interface A   // C3136
// try the following line instead
// _interface A : IUnknown
{
   int a();
};

[object]
__interface B : A
{
   int aa();
};
```
