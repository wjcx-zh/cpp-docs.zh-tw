---
title: 編譯器錯誤 C3457
ms.date: 11/04/2016
f1_keywords:
- C3457
helpviewer_keywords:
- C3457
ms.assetid: 5c1e366a-fa75-4cca-b9a3-86d4ebe4090e
ms.openlocfilehash: 813b1c085cb0464880cb400b6200f9574220bd71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363722"
---
# <a name="compiler-error-c3457"></a>編譯器錯誤 C3457

'attribute': 屬性不支援未具名引數

和 CLR 自訂屬性或編譯器屬性不同，來源附註屬性只支援具名引數。

## <a name="example"></a>範例

下列範例會產生 C3457。

```
#include "SourceAnnotations.h"
[vc_attributes::Post( 1 )] int f();   // C3457
[vc_attributes::Post( Valid=vc_attributes::Yes )] int f2();   // OK
```