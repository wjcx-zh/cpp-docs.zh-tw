---
title: "do-while 陳述式 (C++) | Microsoft Docs"
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
  - "do-while_cpp"
  - "do-while"
  - "do"
  - "while_cpp"
  - "do_cpp"
  - "while"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "do 關鍵字 [C++]"
  - "do 關鍵字 [C++], do-while"
  - "do-while 關鍵字 [C++]"
  - "while 關鍵字 [C++], do-while"
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# do-while 陳述式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

重複執行 *statement* 直到指定的終止條件 \(*expression*\) 判斷值為零。  
  
## 語法  
  
```  
  
      do  
   statement  
   while ( expression ) ;  
```  
  
## 備註  
 終止條件的測試是在每次執行迴圈之後進行；因此，`do-while` 迴圈會執行一次或多次取決於終止運算式的值。  在陳述式主體中執行 [break](../cpp/break-statement-cpp.md)、[goto](../cpp/goto-statement-cpp.md) 或 [return](../cpp/return-statement-cpp.md) 陳述式時，`do-while` 陳述式也可能會終止。  
  
 *expression* 必須有算術或指標類型。  執行程序如下所示：  
  
1.  會執行陳述式主體。  
  
2.  接下來會評估 *expression*。  如果 *expression* 為 false，`do-while` 陳述式會終止，而並將控制項傳遞至程式中的下一個陳述式。  如果 *expression* 為 true \(非零\)，則從步驟 1 開始重複處理序。  
  
## 範例  
 以下範例示範 `do-while` 陳述式：  
  
```  
// do_while_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        printf_s("\n%d",i++);  
    } while (i < 3);  
}  
```  
  
## 請參閱  
 [反覆運算陳述式](../cpp/iteration-statements-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [while 陳述式 \(C\+\+\)](../cpp/while-statement-cpp.md)   
 [for 陳述式 \(C\+\+\)](../cpp/for-statement-cpp.md)   
 [以範圍為基礎的 for 陳述式 \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)