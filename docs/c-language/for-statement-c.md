---
title: "for 陳述式 (C) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "for 關鍵字 [C]"
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# for 陳述式 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`for` 陳述式可讓您依指定的次數重複執行陳述式或複合陳述式。  `for` 陳述式的主體會執行零次或多次，直到的選擇性條件變成 false 為止。  您可以在 `for` 陳述式內使用選擇性的運算式，在 `for` 陳述式的執行期間進行初始化和變更值。  
  
## 語法  
 *iteration\-statement*：  
 `for` \( `init-expression` opt ; `cond-expression`opt ; `loop-expression` opt \)`statement`  
  
 `for` 陳述式的執行如下所述：  
  
1.  評估 `init-expression` \(如果有的話\)。  這會指定迴圈的初始化。  `init-expression` 的類型沒有限制。  
  
2.  評估 `cond-expression` \(如果有的話\)。  此運算式必須是算術或指標類型。  在每個反覆項目之前進行評估。  有三個可能的結果：  
  
    -   如果 `cond-expression` 為 true \(非零\)，則會執行 `statement`，然後再評估 `loop-expression` \(如果有的話\)。  `loop-expression` 會在每個反覆項目之後評估。  其類型沒有限制。  副作用將會依順序執行。  接著會從 `cond-expression` 的評估重新開始此程序。  
  
    -   如果省略 `cond-expression`，則 `cond-expression` 會被視為 true，並依如前面段落中所述的方式繼續執行。  沒有 `cond-expression` 引數的 `for` 陳述式只有在陳述式主體內的 `break` 或 `return` 陳述式執行時，或 `goto` \(移至 `for` 陳述式主體外部的標籤陳述式\) 時才會終止。  
  
    -   如果 `cond-expression` 為 `false` \(0\)，`for` 陳述式會終止，而控制權會傳遞給程式中的下一個陳述式。  
  
 當陳述式主體內的 `break`、`goto` 或 `return` 陳述式執行時，`for` 陳述式也會終止。  `for` 迴圈中的 `continue` 陳述式會造成對於 `loop-expression` 的評估。  當 `for` 迴圈內部的 `break` 陳述式執行時，不會評估也不會執行 `loop-expression`。  此陳述式  
  
```  
for( ;; )  
```  
  
 是產生無限迴圈的慣用方法，其只能使用 `break`、`goto` 或 `return` 陳述式來結束。  
  
## 程式碼  
 這個範例說明 `for` 陳述式：  
  
```  
// c_for.c  
int main()  
{  
   char* line = "H e  \tl\tlo World\0";  
   int space = 0;  
   int tab = 0;  
   int i;  
   int max = strlen(line);  
   for (i = 0; i < max; i++ )   
   {  
      if ( line[i] == ' ' )  
      {  
          space++;  
      }  
      if ( line[i] == '\t' )  
      {  
          tab++;  
      }  
   }  
  
   printf("Number of spaces: %i\n", space);  
   printf("Number of tabs: %i\n", tab);  
   return 0;  
}  
```  
  
## 輸出  
  
```  
Number of spaces: 4  
Number of tabs: 2  
```  
  
## 請參閱  
 [陳述式](../c-language/statements-c.md)