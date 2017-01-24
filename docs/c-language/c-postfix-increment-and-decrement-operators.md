---
title: "C 後置遞增和遞減運算子 | Microsoft Docs"
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
  - "遞增運算子, 語法"
  - "純量運算子"
  - "類型 [C], 純量"
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 後置遞增和遞減運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

後置遞增和遞減運算子的運算元是可修改左值的純量類型。  
  
## 語法  
 *postfix\-expression*：  
 *postfix\-expression*  **\+\+**  
  
 *postfix\-expression*  **––**  
  
 後置遞增或遞減運算的結果為運算元的值。  取得結果之後，運算元的值會遞增 \(或遞減\)。  下列程式碼示範後置遞增運算子。  
  
```  
if( var++ > 0 )  
    *p++ = *q++;  
```  
  
 在此範例中，變數 `var` 會與 0 相比，然後再遞增。  如果 `var` 在遞增前是正數，則會執行下一個陳述式。  首先會將 `q` 所指向的物件值指派給 `p` 所指向的物件。  然後再將 `q` 和 `p` 遞增。  
  
## 請參閱  
 [後置遞增和遞減運算子：\+\+ 和 \-\-](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)