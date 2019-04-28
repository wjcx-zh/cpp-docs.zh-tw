---
title: 編譯器錯誤 C3265
ms.date: 11/04/2016
f1_keywords:
- C3265
helpviewer_keywords:
- C3265
ms.assetid: 10ab3e17-4a9f-4120-bab5-21473869b70f
ms.openlocfilehash: a675567e23764a0b361cab4bef4bc75019de3756
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365841"
---
# <a name="compiler-error-c3265"></a>編譯器錯誤 C3265

不能宣告 managed 'managed 的 construct' unmanaged 'unmanaged 建構' 中

您無法在未受管理的內容中包含的受管理的物件。

下列範例會重現 C3265:

```
// C3265_2.cpp
// compile with: /clr /LD
#include <vcclr.h>

ref class A { };

class B
// try the following line instead
// ref class B
{
   A ^a;   // C3265
   // or embed the managed handle using gcroot
   // try the following line instead
   // gcroot<A^> a;
};
```
