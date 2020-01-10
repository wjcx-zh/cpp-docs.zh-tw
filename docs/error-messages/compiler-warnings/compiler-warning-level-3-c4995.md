---
title: 編譯器警告（層級3） C4995
ms.date: 11/04/2016
f1_keywords:
- C4995
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
ms.openlocfilehash: c361563c2272da002a0edc185cc924c64f6b5e5c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991669"
---
# <a name="compiler-warning-level-3-c4995"></a>編譯器警告（層級3） C4995

' function '：名稱已標記為 #pragma 已被取代

編譯器發現以 pragma 標記的函式已被[取代](../../preprocessor/deprecated-c-cpp.md)。 未來的版本可能不再支援此函式。 您可以使用[warning](../../preprocessor/warning.md) pragma 關閉此警告（以下範例）。

## <a name="example"></a>範例

下列範例會產生 C4995：

```cpp
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
