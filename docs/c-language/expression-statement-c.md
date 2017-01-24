---
title: "運算陳述式 (C) | Microsoft Docs"
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
  - "運算陳述式"
  - "陳述式, 運算式"
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 運算陳述式 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

執行運算陳述式時，會根據[運算式和指派](../c-language/expressions-and-assignments.md)中所列的規則求出運算式的值。  
  
## 語法  
 *expression\-statement*：  
 *expression*  opt **;**  
  
 在執行下一個陳述式之前，會完成運算式求值的所有副作用。  一個空的運算陳述式稱為 Null 陳述式。  如需詳細資訊，請參閱 [Null 陳述式](../c-language/null-statement-c.md)。  
  
 這些範例示範了運算陳述式。  
  
```  
x = ( y + 3 );            /* x is assigned the value of y + 3  */  
x++;                      /* x is incremented                  */  
x = y = 0;                /* Both x and y are initialized to 0 */  
proc( arg1, arg2 );       /* Function call returning void      */  
y = z = ( f( x ) + 3 );   /* A function-call expression        */  
```  
  
 在最後一個陳述式中，函式呼叫運算式、運算式的值 \(包括由函式傳回的所有值\) 會增加 3，然後指派給變數 `y` 和 `z`。  
  
## 請參閱  
 [陳述式](../c-language/statements-c.md)