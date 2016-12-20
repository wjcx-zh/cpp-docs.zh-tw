---
title: "供運算子 &#39;&lt;運算子符號&gt;&#39; 使用的類型 Object 的運算元；可能發生執行階段錯誤 | Microsoft Docs"
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
  - "BC42019"
  - "vbc42019"
helpviewer_keywords: 
  - "BC42019"
ms.assetid: f61944ba-863b-4a82-aae4-249bda52ec8d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 供運算子 &#39;&lt;運算子符號&gt;&#39; 使用的類型 Object 的運算元；可能發生執行階段錯誤
運算式所使用之運算子中的一個或兩個運算元屬於 [Object Data Type](../Topic/Object%20Data%20Type.md)。  
  
 變數或運算式評估為 `Object` 時，編譯器必須執行*「晚期繫結」*\(late binding\)，因而導致執行階段的額外作業。 它也可能會讓您的應用程式發生執行階段錯誤。 例如，假設您將 <xref:System.Windows.Forms.Form> 指派給 `Object` 變數，然後嘗試搭配 [\/ Operator](../Topic/-%20Operator%20\(Visual%20Basic\)3.md) 使用。 如果您這樣做，執行階段會擲回 <xref:System.InvalidCastException>，因為 Visual Basic 無法將 <xref:System.Windows.Forms.Form> 物件轉換成數值。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42019  
  
### 更正這個錯誤  
  
-   如果可能的話，請排列運算元，使其評估為已定義運算子的資料類型。  
  
## 請參閱  
 [Arithmetic Operators in Visual Basic](../Topic/Arithmetic%20Operators%20in%20Visual%20Basic.md)