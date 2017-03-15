---
title: "while 陳述式 (C++) | Microsoft Docs"
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
  - "while_cpp"
  - "while"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "while 關鍵字 [C++]"
  - "while 關鍵字 [C++], 語法"
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# while 陳述式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

重複執行 *陳述式* 直到 *運算式* 為零。  
  
## 語法  
  
```  
  
      while ( expression )  
   statement  
```  
  
## 備註  
 *陳述式*的測試會在每個迴圈執行之前運算; 因此一個 `while` 迴圈會執行零次或一次以上。  *運算式* 必須是整數類別的資料型別、指標型別或一個類別型別且具有明確轉換為整數型別或指標型別。  
  
 當[break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), 或是 [return](../cpp/return-statement-cpp.md)在陳述式被執行時，一個`while`迴圈也可能終止。  使用 [continue](../cpp/continue-statement-cpp.md) 結束正在執行的陳述式，但不需要結束 `while` 迴圈。  **continue** 傳遞控制項到下一階段的`while`迴圈。  
  
 下列程式碼使用 `while` 迴圈調整多出來的字串結尾底線:  
  
```  
// while_statement.cpp  
  
#include <string.h>  
#include <stdio.h>  
char *trim( char *szSource )  
{  
    char *pszEOS = 0;  
  
    //  Set pointer to character before terminating NULL  
    pszEOS = szSource + strlen( szSource ) - 1;  
  
    //  iterate backwards until non '_' is found   
    while( (pszEOS >= szSource) && (*pszEOS == '_') )  
        *pszEOS-- = '\0';  
  
    return szSource;  
}  
int main()  
{  
    char szbuf[] = "12345_____";  
  
    printf_s("\nBefore trim: %s", szbuf);  
    printf_s("\nAfter trim: %s\n", trim(szbuf));  
}  
```  
  
 終止條件的成立與否位在迴圈的最上方。  如果沒有多出來的底線，則此迴圈不會被執行。  
  
## 請參閱  
 [反覆運算陳述式](../cpp/iteration-statements-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [do\-while 陳述式 \(C\+\+\)](../cpp/do-while-statement-cpp.md)   
 [for 陳述式 \(C\+\+\)](../cpp/for-statement-cpp.md)   
 [以範圍為基礎的 for 陳述式 \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)