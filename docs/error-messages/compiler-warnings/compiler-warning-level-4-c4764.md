---
title: 編譯器警告 (層級 4) C4764
ms.date: 11/04/2016
f1_keywords:
- C4764
helpviewer_keywords:
- C4764
ms.assetid: 7bd4296f-966b-484c-bf73-8dbc8e85b4a9
ms.openlocfilehash: 28672d2271e380f6a8240bff98326d5334a0f98f
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989188"
---
# <a name="compiler-warning-level-4-c4764"></a>編譯器警告 (層級 4) C4764

無法對齊超過 16 位元組的攔截物件

已指定大於 16 的對齊，但是在某些平台，如果函式擲回例外狀況，堆疊就會強制不大於 16 的對齊方式。

## <a name="example"></a>範例

下列範例會產生 C4764：

```cpp
// C4764.cpp
// compile with: /W4 /EHsc
// processor: x64 IPF
#include <stdio.h>

class A
{
public:
    int x;
};

typedef __declspec(align(32)) A ALIGNEDA;

int main()
{
    ALIGNEDA a;
    try
    {
        a.x = 15;
        throw a;
    }
    catch (ALIGNEDA b) // can’t align b to > 16 bytes
    {
        printf_s("%d\n", b.x);
    }
}   // C4764
```
