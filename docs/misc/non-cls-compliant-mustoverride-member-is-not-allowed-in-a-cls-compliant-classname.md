---
title: "符合 CLS 標準的 &#39;&lt;類別名稱&gt;&#39; 中不允許不符合 CLS 標準的 &#39;MustOverride&#39; 成員 | Microsoft Docs"
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
  - "bc40034"
  - "vbc40034"
helpviewer_keywords: 
  - "BC40034"
ms.assetid: 4eb36b3a-1bbe-4e99-9ecb-a12b8729b128
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 符合 CLS 標準的 &#39;&lt;類別名稱&gt;&#39; 中不允許不符合 CLS 標準的 &#39;MustOverride&#39; 成員
類別標記為 `<CLSCompliant(True)>`，但它包含標記為 `<CLSCompliant(False)>` 或未標記的 `MustOverride` 屬性或程序。  
  
 當類別符合 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 時，使用該類別的應用程式只會存取標記為 `<CLSCompliant(True)>` 的成員，並忽略別的成員。 不過，應用程式不能忽視 `MustOverride` 屬性或程序，因為它必須存取該屬性或程序才能覆寫它。  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40034  
  
### 更正這個錯誤  
  
-   如果您需要 CLS 符合性，而且能夠控制類別原始程式碼，請將成員標記為 `<CLSCompliant(True)>`。  
  
-   如果需要 CLS 符合性，而且不需要控制類別原始程式碼，或是它不符合 CLS 標準，請在不同的類別內定義這個成員。  
  
-   如果您需要此成員保持不相容，請從其定義移除 `MustOverride` 關鍵字、從類別定義移除 <xref:System.CLSCompliantAttribute>，或將類別標記為 `<CLSCompliant(False)>`。  
  
## 請參閱  
 [MustOverride](../Topic/MustOverride%20\(Visual%20Basic\).md)   
 [\<PAVE OVER\> 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)