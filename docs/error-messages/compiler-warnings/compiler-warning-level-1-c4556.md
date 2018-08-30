---
title: 編譯器警告 （層級 1） C4556 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- xml
- C4556
dev_langs:
- C++
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 987e4dc3ba6aea7dcb01dc05cd94c45baced05b8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211024"
---
# <a name="compiler-warning-level-1-c4556"></a>編譯器警告 (層級 1) C4556

> 內建函式直接引數的值 '*值*'je mimo rozsah'*lowerbound* - *上界*'

## <a name="remarks"></a>備註

內建符合一個硬體指令。 硬體指令有固定的數目的位元編碼常數。 如果*值*是超出範圍，它不會編碼正確。 編譯器會截斷額外的位元。

## <a name="example"></a>範例

下列範例會產生 C4556:

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