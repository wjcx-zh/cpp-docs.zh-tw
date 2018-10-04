---
title: 編譯器錯誤 C3136 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3136
dev_langs:
- C++
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 082a89b69092a8320f6bb4b930d01a7fd2de10c8
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788379"
---
# <a name="compiler-error-c3136"></a>編譯器錯誤 C3136

'interface': COM 介面只可以繼承自其他 COM 介面、 'interface' 不是 COM 介面

在您套用至介面[interface 屬性](../../windows/attributes/interface-attributes.md)繼承自不是 COM 介面的介面。 COM 介面最終繼承自`IUnknown`。 任何加上介面屬性的介面是 COM 介面。

下列範例會產生 C3136:

```
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