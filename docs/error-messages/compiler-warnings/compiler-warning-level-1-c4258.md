---
title: 編譯器警告 （層級 1） C4258 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4258
dev_langs:
- C++
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08a182ed592119fd52247737988810f9ca66b45c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4258"></a>編譯器警告 (層級 1) C4258
'variable': 從定義迴圈會忽略;封閉範圍的定義使用 」  
  
 在下[/Ze](../../build/reference/za-ze-disable-language-extensions.md)和[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)中, 定義的變數[如](../../cpp/for-statement-cpp.md)迴圈超出範圍**的**迴圈結束。 如果迴圈變數，但在封閉迴圈中，定義與同名的變數會再次使用中包含的範圍，就會發生這個警告**如**迴圈。 例如:   
  
```  
// C4258.cpp  
// compile with: /Zc:forScope /W1  
int main()  
{  
   int i;  
   {  
      for (int i =0; i < 1; i++)  
         ;  
      i = 20;   // C4258 i (in for loop) has gone out of scope  
   }  
}  
```