---
title: "do-while 陳述式 (C) | Microsoft Docs"
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
  - "do"
  - "while"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "do-while 關鍵字 [C]"
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# do-while 陳述式 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`do-while` 陳述式可讓您重複陳述式或複合陳述式，直到指定的運算式變成 false 為止。  
  
## 語法  
 *iteration\-statement*：  
 **do**  *statement*  **while \(**  *expression*  **\) ;**  
  
 執行迴圈的主體後，會評估 `do-while` 陳述式中的 *expression*。  因此，迴圈主體一律至少執行一次。  
  
 *expression* 必須有算術或指標類型。  執行程序如下所示：  
  
1.  會執行陳述式主體。  
  
2.  接下來會評估 *expression*。  如果 *expression* 為 false，`do-while` 陳述式會終止，而並將控制項傳遞至程式中的下一個陳述式。  如果 *expression* 為 true \(非零\)，則從步驟 1 開始重複處理序。  
  
 在陳述式主體中執行 **break**、`goto` 或 `return` 陳述式時，`do-while` 陳述式也可能會終止。  
  
 這是 `do-while` 陳述式的範例：  
  
```  
do   
{  
    y = f( x );  
    x--;  
} while ( x > 0 );  
```  
  
 在這個 `do-while` 陳述式中，會執行 `y = f( x );` 和 `x--;` 兩個陳述式，無論 `x` 的初始值為何。  接下來會評估 `x > 0`。  如果 `x` 大於 0，會再次執行陳述式主體，並重新評估 `x > 0`。  只要 `x` 保持大於 0，陳述式主體就會重複執行。  `x` 變成 0 或負值時，`do-while` 陳述式會終止執行。  迴圈主體至少執行一次。  
  
## 請參閱  
 [do\-while 陳述式 \(C\+\+\)](../cpp/do-while-statement-cpp.md)