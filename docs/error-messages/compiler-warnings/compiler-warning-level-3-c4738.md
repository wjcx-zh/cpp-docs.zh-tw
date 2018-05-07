---
title: 編譯器警告 (層級 3) C4738 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4738
dev_langs:
- C++
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50b94cde2f8809b8ce56dc599804d11b8d058166
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4738"></a>編譯器警告 (層級 3) C4738
在記憶體中儲存 32 位元浮點結果，可能會損失效能  
  
 C4738 警告的設定、 轉型，結果會傳遞引數，或其他作業可能需要進行捨入，或作業已用盡暫存器，並且需要使用 （溢出） 的記憶體。 這樣可以降低效能。  
  
 若要解決這個警告，並避免進位，以編譯[/fp: fast](../../build/reference/fp-specify-floating-point-behavior.md)或使用`double`而不是`float`。  
  
 若要解決這個警告，並避免完暫存器，變更計算的順序和修改貴用戶使用內嵌  
  
 此警告預設為關閉。 如需詳細資訊，請參閱 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4738:  
  
```  
// C4738.cpp  
// compile with: /c /fp:precise /O2 /W3  
// processor: x86  
#include <stdio.h>  
  
#pragma warning(default : 4738)  
  
float func(float f)  
{  
    return f;  
}  
  
int main()  
{  
    extern float f, f1, f2;  
    double d = 0.0;  
  
    f1 = func(d);  
    f2 = (float) d;  
    f = f1 + f2;   // C4738  
    printf_s("%f\n", f);  
}  
```