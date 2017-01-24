---
title: "if-else 陳述式 (C++) | Microsoft Docs"
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
  - "else_cpp"
  - "else"
  - "if_cpp"
  - "if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "else 關鍵字 [C++]"
  - "if 關鍵字 [C++]"
  - "if 關鍵字 [C++], if-else"
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# if-else 陳述式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控制條件分支。  
  
## 語法  
  
```  
  
      if ( expression )  
   statement1  
[else  
   statement2]  
```  
  
## 備註  
 如果 *運算式* 的值為非零值， 執行*statement1* 。  如果選擇性的 **else** 存在， *statement2* 執行，如果 *運算式* 式的值為零。  *運算式* 必須是算術或指標型別，或者必須是有明確定義轉換到算術或指標型別的類別。\(如需轉換的詳細資訊，請參閱[標準轉換](../cpp/standard-conversions.md)\)。  
  
 **if** 陳述式的兩種形式， *運算式*，可以是除了結構的所有值，包括任何副作用。  除非其中一個 *陳述式*包含 [break](../cpp/break-statement-cpp.md)、 [continue](../cpp/continue-statement-cpp.md)或 [goto](../cpp/goto-statement-cpp.md)，將控制項從 **if** 陳述式傳遞至程式的下一個陳述式。  
  
 `if...else` 陳述式的 **else** 子句與最接近沒有與其它 **if** 陳述句在相同範圍中的 **else** 陳述句相組。  
  
 若要讓這個範例可以明確的表示 `if...else` 對，將註釋除去。  
  
## 範例  
  
```  
// if_else_statement.cpp  
#include <stdio.h>  
  
int main()   
{  
   int x = 0;  
   if (x == 0)  
   {  
      printf_s("x is 0!\n");  
   }  
   else  
   {  
      printf_s("x is not 0!\n"); // this statement will not be executed  
   }  
  
   x = 1;  
   if (x == 0)  
   {  
      printf_s("x is 0!\n"); // this statement will not be executed  
   }  
   else  
   {  
      printf_s("x is not 0!\n");  
   }  
  
   return 0;  
}  
```  
  
  **x 是 0\!**  
**x 不是 0\!**   
## 請參閱  
 [選擇陳述式](../cpp/selection-statements-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [switch 陳述式 \(C\+\+\)](../cpp/switch-statement-cpp.md)