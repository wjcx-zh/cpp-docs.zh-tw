---
title: "System.CLSCompliantAttribute 無法套用至屬性 &#39;Get&#39;/&#39;Set&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40043"
  - "BC40043"
helpviewer_keywords: 
  - "BC40043"
ms.assetid: 2ff45c09-32be-4ca9-b42a-63ce2536db7d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.CLSCompliantAttribute 無法套用至屬性 &#39;Get&#39;/&#39;Set&#39;
屬性定義會將 <xref:System.CLSCompliantAttribute> 屬性套用至其 `Get` 或 `Set` 陳述式。  
  
 屬性若要符合 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\)，則整個屬性都必須標記為 `<CLSCompliant(True)>`。 您必須將 <xref:System.CLSCompliantAttribute> 套用至 [Property Statement](../Topic/Property%20Statement.md)，非而套用至 `Get` 或 `Set` 陳述式。  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID：**BC40043  
  
### 更正這個錯誤  
  
-   從 `Get` 或 `Set` 陳述式移除 <xref:System.CLSCompliantAttribute>。  
  
-   如果屬性應該符合 CLS 標準，請將 `Property` 陳述式標記為 `<CLSCompliant(True)>`。  
  
## 請參閱  
 [\<PAVE OVER\> 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Get Statement](../Topic/Get%20Statement.md)   
 [Set Statement](../Topic/Set%20Statement%20\(Visual%20Basic\).md)