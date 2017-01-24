---
title: "continue 陳述式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "continue"
  - "continue_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "continue 關鍵字 [C++]"
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# continue 陳述式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

強制將控制項傳輸至最小的封閉 [do](../cpp/do-while-statement-cpp.md)、[for](../cpp/for-statement-cpp.md) 或 [while](../cpp/while-statement-cpp.md) 迴圈之控制運算式。  
  
## 語法  
  
```  
continue;  
```  
  
## 備註  
 目前反覆項目中其餘的任何陳述式都不會執行。  迴圈中下一個反覆項目的判斷方式如下：  
  
-   在 `do` 或 `while` 迴圈中，下一個反覆項目是藉由重新計算 `do` 或 `while` 陳述式的控制運算式的值開始。  
  
-   在 `for` 迴圈中 \(使用語法 `for`\(`init-expr`; `cond-expr`; `loop-expr`\)\) 會執行 `loop-expr` 子句。  然後會重新求出 `cond-expr` 子句的值，而根據結果，迴圈會結束或另一個反覆項目會發生。  
  
 下列範例將示範如何使用 `continue` 陳述式略過程式碼區段及開始迴圈的下一個反覆項目。  
  
## 範例  
  
```  
// continue_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        i++;  
        printf_s("before the continue\n");  
        continue;  
        printf("after the continue, should never print\n");  
     } while (i < 3);  
  
     printf_s("after the do loop\n");  
}  
```  
  
  **before the continue**  
**before the continue**  
**before the continue**  
**after the do loop**   
## 請參閱  
 [跳躍陳述式](../cpp/jump-statements-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)