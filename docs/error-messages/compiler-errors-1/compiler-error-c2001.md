---
title: "編譯器錯誤 C2001 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2001"
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

常數中包含新行字元  
  
 您必須依照下列方式才能使字串常數繼續到第二行：  
  
-   利用反斜線結束第一行。  
  
-   利用雙引號來結束第一行的字串，然後利用另一個雙引號來開啟下一行的字串。  
  
 使用 \\n 並無法結束第一行。  
  
## 範例  
 下列範例會產生 C2001：  
  
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
  
## 範例  
 行接續字元 \(Line\-Continuation Character\) 後的下一行起始空白將會包含於字串常數內。  上述範例中沒有一個會將新行字元 \(Newline Character，\\n\) 嵌入於字串常數。  您可依下列範例來嵌入新行字元：  
  
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