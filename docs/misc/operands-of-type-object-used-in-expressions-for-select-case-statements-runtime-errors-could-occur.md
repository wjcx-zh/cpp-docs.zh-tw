---
title: "&#39;Select&#39;、&#39;Case&#39; 陳述式的運算式中所使用的類型 Object 的運算元; 可能發生執行階段錯誤 | Microsoft Docs"
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
  - "vbc42036"
  - "bc42036"
helpviewer_keywords: 
  - "BC42036"
ms.assetid: f11e9c9f-aa66-4eb1-8f49-abf713bef885
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Select&#39;、&#39;Case&#39; 陳述式的運算式中所使用的類型 Object 的運算元; 可能發生執行階段錯誤
`Select`...`Case` 結構使用一或多個[Object Data Type](../Topic/Object%20Data%20Type.md)的運算式。  
  
 變數或運算式評估為 `Object` 時，編譯器必須執行*「晚期繫結」*\(late binding\)，因而導致執行階段的額外作業。 它也可能會讓您的應用程式發生執行階段錯誤。 例如，如果您將 <xref:System.Windows.Forms.Form> 指派給 `Object` 變數，然後嘗試將它與數字比較，則執行階段會擲回 <xref:System.InvalidCastException>，因為 Visual Basic 無法將 <xref:System.Windows.Forms.Form> 物件轉換成數值。  
  
 `Select`...`Case` 建構中的運算式應該全部是相同的資料類型，或可以相互轉換、密切相關的資料類型。 這是因為每個 `Case` 陳述式會針對 `Select`...`Case` 建構所根據的測試運算式，至少比較一個值。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42036  
  
### 更正這個錯誤  
  
-   可能的話，請排列所有運算式，以評估為其定義比較運算子的資料類型。  
  
## 請參閱  
 [Select...Case Statement](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)   
 [Arithmetic Operators in Visual Basic](../Topic/Arithmetic%20Operators%20in%20Visual%20Basic.md)   
 [Comparison Operators in Visual Basic](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)