---
title: "while 陳述式 (C) | Microsoft Docs"
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
  - "while"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "while 關鍵字 [C]"
  - "while 關鍵字 [C], 語法"
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# while 陳述式 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`while` 陳述式可讓您重複陳述式直到指定的運算式變成 false 為止。  
  
## 語法  
 *iteration\-statement*：  
 **while \(**  *expression*  **\)**  *statement*  
  
 *expression* 必須有算術或指標類型。  執行程序如下所示：  
  
1.  會對 *expression* 進行評估。  
  
2.  如果 *expression* 一開始是 false，就永遠不會執行 `while` 陳述式的主體，且控制項會從 `while` 陳述式傳遞至程式的下一個陳述式。  
  
     如果 *expression* 為 true \(非零\)，就會執行陳述式的本體，且從步驟 1 開始重複處理序。  
  
 `while` 陳述式也可能會在陳述式本體中的 **break**、`goto` 或 `return` 執行時終止。  請使用 **continue** 陳述式終止反覆項目而不結束 `while` 迴圈。  **continue** 陳述式會將控制項傳遞至 `while` 陳述式的下一個反覆項目。  
  
 這是 `while` 陳述式的範例：  
  
```  
while ( i >= 0 )   
{  
    string1[i] = string2[i];  
    i--;  
}  
```  
  
 這個範例會將 `string2` 的字元複製到 `string1`。  如果 `i` 大於或等於 0，會將 `string2[i]` 指派給 `string1[i]` 並遞減 `i`。  當 `i` 等於或小於 0 時，會終止執行 `while` 陳述式。  
  
## 請參閱  
 [while 陳述式 \(C\+\+\)](../cpp/while-statement-cpp.md)