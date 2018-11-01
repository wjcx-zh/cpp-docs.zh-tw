---
title: 編譯器錯誤 C3117
ms.date: 11/04/2016
f1_keywords:
- C3117
helpviewer_keywords:
- C3117
ms.assetid: dceee392-d4c7-4599-b75e-7aaac7c36fdd
ms.openlocfilehash: 66efcf95599a18e0d93ff36f0e684ad350941977
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486121"
---
# <a name="compiler-error-c3117"></a>編譯器錯誤 C3117

'%$S': 介面只可以有一個基底類別

您宣告多個基底類別會繼承的介面。

下列範例會產生 C3117:

```
// C3117.cpp
#include <windows.h>

[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface I1
{
};

[ object, uuid("00000000-0000-0000-0000-000000000002") ]
__interface I2
{
};

[ object, uuid("00000000-0000-0000-0000-000000000003") ]
__interface I3 : I1, I2
{   // C3117
};
```