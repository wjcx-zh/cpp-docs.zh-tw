---
title: 編譯器警告 (層級 1) C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: 00526b3dae5035fe96ec1abb50bbdd056ceecfaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538526"
---
# <a name="compiler-warning-level-1-c4939"></a>編譯器警告 (層級 1) C4939

\#pragma vtordisp 已被取代，將在未來的 Visual c + + 版本中移除

[vtordisp](../../preprocessor/vtordisp.md) pragma 會在未來的 Visual C++ 版本中予以移除。

## <a name="example"></a>範例

下列範例會產生 C4939。

```
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```