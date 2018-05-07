---
title: 編譯器錯誤 C2001 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2001
dev_langs:
- C++
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f56eabbcb5ca322d7549c21a56893a8e13d9261
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2001"></a>編譯器錯誤 C2001
常數中的新行  
  
 字串常數，無法繼續第二行，除非您執行下列作業：  
  
-   結尾的第一行以反斜線。  
  
-   關閉第一個列中利用雙引號字串並在下一行的字串以開啟另一個雙引號。  
  
 結束 \n 的第一行是不夠的。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2001:  
  
```  
// C2001.cpp  
// C2001 expected  
#include <stdio.h>  
  
int main()  
{  
    printf_s("Hello,  
             world");  
    printf_s("Hello,\n  
             world");  
}  
```  
  
## <a name="example"></a>範例  
 行接續符號字元之後的下一行的開頭的空格會包含在字串常數。 無如上所示的範例會將新行字元嵌入字串常數。 您可以將內嵌的新行字元，如下所示：  
  
```  
// C2001b.cpp  
#include <stdio.h>  
  
int main()  
{  
    printf_s("Hello,\n\  
             world");  
  
    printf_s("Hello,\  
             \nworld");  
  
    printf_s("Hello,\n"  
             "world");  
  
    printf_s("Hello,"  
             "\nworld");  
  
    printf_s("Hello,"  
             " world");  
  
    printf_s("Hello,\  
             world");  
}  
```