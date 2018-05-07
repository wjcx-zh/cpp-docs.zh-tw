---
title: 編譯器警告 （層級 3） C4414 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4414
dev_langs:
- C++
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1526b20732d7a1b08ec8d753cb64e33e42dd809
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4414"></a>編譯器警告 (層級 3) C4414
'function': 函式的 short 跳躍指令被轉換為 near  
  
 Short 跳躍點產生精簡指令，從指令分支為有限範圍內的位址。 指示包含簡短的位移，代表跳躍和目標位址，函式定義之間的距離。 在連結函式可能會移動，或因移出範圍可從簡短的位移，函式會連結時間最佳化。 編譯器必須產生一種特殊記錄，這需要是不久或目前的 jmp 指令跳躍。 編譯器會進行轉換。  
  
 例如，下列程式碼會產生 C4414:  
  
```  
// C4414.cpp  
// compile with: /W3 /c  
// processor: x86  
int DoParityEven();  
int DoParityOdd();  
unsigned char global;  
int __declspec(naked) DoParityEither()  
{  
   __asm  
   {  
      test global,0  
      jpe SHORT DoParityEven  // C4414  
      jmp SHORT DoParityOdd   // C4414  
   }  
}  
```