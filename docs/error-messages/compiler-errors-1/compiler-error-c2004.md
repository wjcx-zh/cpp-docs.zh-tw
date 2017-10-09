---
title: "編譯器錯誤 C2004 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2004
dev_langs:
- C++
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: f4596e43fad713f6b0a81eea9e697c6e0f91c75b
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2004"></a>編譯器錯誤 C2004
必須是 'defined(id)'  
  
 識別項必須出現在括弧中，後面接著前置處理器關鍵字。  
  
 針對 Visual Studio .NET 2003 所進行的編譯器一致性工作，也可能會導致這個錯誤：前置處理器指示詞中遺漏括弧。 如果前置處理器指示詞中遺漏右括弧，編譯器會產生錯誤。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2004：  
  
```  
// C2004.cpp  
// compile with: /DDEBUG  
#include <stdio.h>  
  
int main()   
{  
    #if defined(DEBUG   // C2004  
        printf_s("DEBUG defined\n");  
    #endif  
}  
```  
  
## <a name="example"></a>範例  
 可能的解決方式：  
  
```  
// C2004b.cpp  
// compile with: /DDEBUG  
#include <stdio.h>  
  
int main()   
{  
    #if defined(DEBUG)  
        printf_s("DEBUG defined\n");  
    #endif  
}  
```
