---
title: 編譯器警告 （層級 1） C4556 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 22d10f7dc73e0d5e39fcad8975114f7cb176b24d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282908"
---
# <a name="compiler-warning-level-1-c4556"></a>編譯器警告 (層級 1) C4556
內建函式直接引數 'value' 的值超出範圍 'lowerbound-upperbound'  
  
 內建函式符合硬體指令。 硬體指令具有固定的數目的編碼常數的位元。 如果***值***是超出範圍，它將不會編碼正確。 編譯器會截斷額外的位元。  
  
 下列範例會產生 C4556:  
  
```  
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