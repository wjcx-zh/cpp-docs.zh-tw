---
title: "編譯器警告 （層級 1） C4258 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4258
dev_langs: C++
helpviewer_keywords: C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 436ef3dd9984750885390a3974572b9d86bd7243
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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