---
title: "goto 和標記陳述式 (C) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "goto"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "goto 關鍵字 [C]"
  - "labeled 陳述式"
  - "陳述式, 已標記"
ms.assetid: 3d0473dc-4b18-4fcc-9616-31a38499d7d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# goto 和標記陳述式 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`goto` 陳述式會將控制項傳輸至標籤。  所指的標籤必須位於相同的函式中，而且只能出現在相同函式中的單獨一個陳述式前面。  
  
## 語法  
 *statement*:  
 *labeled\-statement*  
  
 *jump\-statement*  
  
 *jump\-statement*：  
 **goto**  *identifier*  **;**  
  
 *labeled\-statement*：  
 *identifier*  **:**  *statement*  
  
 陳述式標籤只對 `goto` 陳述式有意義，在任何其他內容中，加上標籤的陳述式都會執行，而不考慮標籤。  
  
 *jump\-statement* 必須位於相同的函式中，而且只能出現在相同函式中的單獨一個陳述式前面。  `goto` 後面的一組 *identifier* 名稱都有自己的命名空間，因此這些名稱不會干擾其他識別項。  標籤不能重新宣告。  如需詳細資訊，請參閱[命名空間](../c-language/name-spaces.md)。  
  
 理想的程式設計風格是盡可能先使用 **break**、**continue** 和 `return` 陳述式，而不是 `goto`。  由於 **break** 陳述式只會從一個迴圈層級結束，因此可能需要有 `goto` 才能從深層的巢狀迴圈內結束迴圈。  
  
 這個範例將示範 `goto` 陳述式：  
  
```  
// goto.c  
#include <stdio.h>  
  
int main()  
{  
    int i, j;  
  
    for ( i = 0; i < 10; i++ )  
    {  
        printf_s( "Outer loop executing. i = %d\n", i );  
        for ( j = 0; j < 3; j++ )  
        {  
            printf_s( " Inner loop executing. j = %d\n", j );  
            if ( i == 5 )  
                goto stop;  
        }  
    }  
  
    /* This message does not print: */  
    printf_s( "Loop exited. i = %d\n", i );  
  
    stop: printf_s( "Jumped to stop. i = %d\n", i );  
}  
```  
  
 在這個範例中，當 `i` 等於 5 時，`goto` 陳述式會將控制項傳送至標記 `stop` 的點。  
  
## 請參閱  
 [陳述式](../c-language/statements-c.md)