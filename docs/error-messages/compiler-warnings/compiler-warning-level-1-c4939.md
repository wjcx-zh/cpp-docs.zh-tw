---
title: 編譯器警告 (層級 1) C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: 5c87dad744281464599ee6c28b5bcf6e350b9feb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199273"
---
# <a name="compiler-warning-level-1-c4939"></a>編譯器警告 (層級 1) C4939

\#pragma vtordisp 已被取代，將在未來的 Visual 版本中移除C++

[vtordisp](../../preprocessor/vtordisp.md) pragma 會在未來的 Visual C++ 版本中予以移除。

## <a name="example"></a>範例

下列範例會產生 C4939。

```cpp
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```
