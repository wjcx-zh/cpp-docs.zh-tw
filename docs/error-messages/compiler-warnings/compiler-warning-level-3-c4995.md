---
title: 編譯器警告 （層級 3） C4995
ms.date: 11/04/2016
f1_keywords:
- C4995
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
ms.openlocfilehash: 54bc8931b5eaa3bbb5053e5c21aa2aaaa73126fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401510"
---
# <a name="compiler-warning-level-3-c4995"></a>編譯器警告 （層級 3） C4995

'function': 名稱被標示為已被取代的 #pragma

編譯器遇到函式已標記為 pragma[已被取代](../../preprocessor/deprecated-c-cpp.md)。 未來的版本可能不再支援此函式。 您可以關閉此警告，與[警告](../../preprocessor/warning.md)pragma （下面的範例）。

## <a name="example"></a>範例

下列範例會產生 C4995:

```
// C4995.cpp
// compile with: /W3
#include <stdio.h>

// #pragma warning(disable : 4995)
void func1(void)
{
    printf("\nIn func1");
}

int main()
{
    func1();
    #pragma deprecated(func1)
    func1();   // C4995
}
```