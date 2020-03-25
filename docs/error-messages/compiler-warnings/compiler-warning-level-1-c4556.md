---
title: 編譯器警告 (層級 1) C4556
ms.date: 08/27/2018
f1_keywords:
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: 501d79a8a86fcd3e2d8ba08dc2f03488f9abb827
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162305"
---
# <a name="compiler-warning-level-1-c4556"></a>編譯器警告 (層級 1) C4556

> 內建函式直接引數 '*value*' 的值超出 '*lowerbound* - *界*' 範圍

## <a name="remarks"></a>備註

內建函式符合硬體指令。 硬體指令具有固定數目的位數，以編碼常數。 如果*值*超出範圍，則不會正確編碼。 編譯器會截斷額外的位。

## <a name="example"></a>範例

下列範例會產生 C4556：

```cpp
// C4556.cpp
// compile with: /W1
// processor: x86 IPF
#include <xmmintrin.h>

void test()
{
   __m64 m;
   _m_pextrw(m, 5);   // C4556
}

int main()
{
}
```
