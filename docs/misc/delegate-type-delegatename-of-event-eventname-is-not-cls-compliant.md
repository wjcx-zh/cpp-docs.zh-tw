---
title: "事件 &#39;&lt;事件名稱&gt;&#39; 的委派類型 &#39;&lt;委派名稱&gt;&#39; 不符合 CLS 標準 | Microsoft Docs"
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
  - "bc40050"
  - "vbc40050"
helpviewer_keywords: 
  - "BC40050"
ms.assetid: 92f5be26-9a82-46d4-bf97-005f2c7ca424
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 事件 &#39;&lt;事件名稱&gt;&#39; 的委派類型 &#39;&lt;委派名稱&gt;&#39; 不符合 CLS 標準
[Event Statement](../Topic/Event%20Statement.md) 使用委派來指定其簽章，但 [Delegate Statement](../Topic/Delegate%20Statement.md) 已標記為 `<CLSCompliant(False)>` 或未標記。  
  
 將 <xref:System.CLSCompliantAttribute> 屬性套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40050  
  
### 更正這個錯誤  
  
-   如果您必須符合 CLS 標準，而且可以控制委派的定義，請將 <xref:System.CLSCompliantAttribute> 套用至其宣告，以將其標記為 `<CLSCompliant(True)>`。  
  
-   如果您無法控制委派的定義，或無法將其標記為符合標準，請從 `Event` 陳述式中移除 <xref:System.CLSCompliantAttribute>，或將其標記為 `<CLSCompliant(False)>`。  
  
## 請參閱  
 [\<PAVE OVER\> 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)