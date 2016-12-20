---
title: "&#39;Implements&#39; 在運算子宣告中無效 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33004"
  - "bc33004"
helpviewer_keywords: 
  - "BC33004"
ms.assetid: 22f27f4d-4bbd-4f8f-a6e8-0fc10efb268d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Implements&#39; 在運算子宣告中無效
[Operator Statement](../Topic/Operator%20Statement.md) 指定 [Implements](../Topic/Implements%20Clause%20\(Visual%20Basic\).md) 關鍵字。  
  
 只有 `Function` 或 `Sub` 程序、屬性或事件才能實作介面成員。 如需實作的詳細資訊，請參閱[不在組建中：在 Visual Basic 中的介面實作範例](http://msdn.microsoft.com/zh-tw/50bf2a30-73b6-4126-a921-075fd6eec278)。  
  
 `Operator` 程序需要 `Public` 和 `Shared` 關鍵字，而轉換運算子需要 `Widening` 或 `Narrowing` 關鍵字。 如需詳細資訊，請參閱[Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)。  
  
 **錯誤 ID︰**BC33004  
  
### 更正這個錯誤  
  
-   如果您想要這個程序來實作介面成員，請將它重寫為 `Function` 或 `Sub` 程序、屬性或事件。  
  
-   如果您想要讓這個程序定義運算子，請從其宣告移除 `Implements` 關鍵字。  
  
## 請參閱  
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)