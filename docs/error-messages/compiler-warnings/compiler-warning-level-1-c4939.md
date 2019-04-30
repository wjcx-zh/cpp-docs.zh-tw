---
title: 編譯器警告 (層級 1) C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: 00526b3dae5035fe96ec1abb50bbdd056ceecfaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408247"
---
# <a name="compiler-warning-level-1-c4939"></a>編譯器警告 (層級 1) C4939

\#pragma vtordisp 已被取代，將視覺效果的未來版本中移除C++

[vtordisp](../../preprocessor/vtordisp.md) pragma 會在未來的 Visual C++ 版本中予以移除。

## <a name="example"></a>範例

下列範例會產生 C4939。

```
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```