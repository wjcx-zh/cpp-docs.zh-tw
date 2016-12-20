---
title: "方法 &#39;&lt;程序名稱&gt;&#39; 的推斷類型引數，導致下列錯誤: &lt;警告清單&gt; | Microsoft Docs"
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
  - "bc41006"
  - "vbc41006"
helpviewer_keywords: 
  - "BC41006"
ms.assetid: c789ffa9-0273-47f6-8915-78fc6a7d3d6d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 &#39;&lt;程序名稱&gt;&#39; 的推斷類型引數，導致下列錯誤: &lt;警告清單&gt;
泛型程序是在未提供任何類型引數的情況下所呼叫，而推斷的類型引數會導致一個或多個警告。  
  
 通常，當您叫用泛型類型時，會針對泛型類型所定義的每個類型參數提供類型引數。 如果您未提供任何類型引數，編譯器會嘗試推斷要傳遞給類型參數的類型。 如果推斷的類型導致模稜兩可，或者它們建立的情況可能導致非預期的結果，則編譯器會產生這個警告。  
  
 類型參數上的*「條件約束」*\(constraint\) 會限制可傳遞給它的類型引數。 例如，可能會將類型參數限制為可實作 <xref:System.IComparable%601> 介面的類別。 如需詳細資訊，請參閱 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)中的＜條件約束＞。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC41006  
  
### 更正這個錯誤  
  
-   請將類型引數提供給泛型程序，這樣編譯器就不需要推斷它們。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)