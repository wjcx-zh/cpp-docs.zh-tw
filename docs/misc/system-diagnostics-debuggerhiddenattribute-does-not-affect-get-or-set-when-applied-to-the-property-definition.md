---
title: "System.Diagnostics.DebuggerHiddenAttribute 在套用至 Property 定義時，並不會影響 &#39;Get&#39; 或 &#39;Set&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40051"
  - "vbc40051"
helpviewer_keywords: 
  - "BC40051"
ms.assetid: 623d5e48-7fb2-48a9-bbbb-92914b08c01c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Diagnostics.DebuggerHiddenAttribute 在套用至 Property 定義時，並不會影響 &#39;Get&#39; 或 &#39;Set&#39;
System.Diagnostics.DebuggerHiddenAttribute 在套用至 Property 定義時，並不會影響 'Get' 或 'Set'。 請依適合的情況直接將屬性 \(attribute\) 套用至 'Get' 和 'Set' 程序。  
  
 <xref:System.Diagnostics.DebuggerHiddenAttribute> 已套用至屬性宣告。  
  
 原始程式碼可將 <xref:System.Diagnostics.DebuggerHiddenAttribute> 套用至程序。 這樣做會指示 Visual Studio 偵錯工具在程序內不停止，而且不允許在程序中設定任何中斷點。  
  
 雖然您可以將 <xref:System.Diagnostics.DebuggerHiddenAttribute> 套用至屬性，但不會有任何作用。 只有在將其套用至屬性的 `Get` 或 `Set` 程序時，才有您需要的作用。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40051  
  
### 更正這個錯誤  
  
-   從屬性宣告中移除 <xref:System.Diagnostics.DebuggerHiddenAttribute>，並依適合的情況將其套用至屬性的 `Get` 或 `Set` 程序。  
  
## 請參閱  
 <xref:System.Diagnostics.DebuggerHiddenAttribute>   
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [Property Statement](../Topic/Property%20Statement.md)   
 [Get Statement](../Topic/Get%20Statement.md)   
 [Set Statement](../Topic/Set%20Statement%20\(Visual%20Basic\).md)