---
title: "運算式遞迴呼叫包含運算子 &#39;&lt;運算子符號&gt;&#39; | Microsoft Docs"
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
  - "BC42004"
  - "vbc42004"
helpviewer_keywords: 
  - "BC42004"
ms.assetid: a874c44a-3aec-447d-90f7-5659f1b2f5f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 運算式遞迴呼叫包含運算子 &#39;&lt;運算子符號&gt;&#39;
運算子程序內的運算式使用所定義的運算子。 這會導致呼叫本身的運算子程序，因為正在使用的資料類型。  
  
 如果您正在定義的運算子程序搭配使用相同的運算子與下列任何一項，則會呼叫本身：  
  
-   您正在定義其運算子的相同運算元；  
  
-   您正在定義其運算子之相同資料類型的運算元；或  
  
-   可擴展至您正在定義其運算子之資料類型的資料類型的運算元。  
  
 *「遞迴呼叫」*\(recursive call\) 是程序呼叫本身時。 遞迴呼叫可能會導致*「無限迴圈」*\(infinite loop\)，其中，控制項會重複通過一組相同的陳述式，直到從外部終止應用程式為止。 如果您的程式碼未包含可用來終止遞迴的一或多個測試，則會有無限迴圈的風險。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42004  
  
### 更正這個錯誤  
  
-   如果您的邏輯需要運算子程序呼叫本身，則請確定您測試至少一個發生在某個時間點的特定條件，並使用這項測試來終止遞迴呼叫。  
  
-   如果您的邏輯不需要運算子程序呼叫本身，則請移除任何遞迴呼叫，或將它們取代為不會呼叫其專屬程序的陳述式。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)