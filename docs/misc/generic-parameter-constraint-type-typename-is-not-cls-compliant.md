---
title: "泛型參數條件約束類型 &lt;類型名稱&gt; 不符合 CLS 標準 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40040"
  - "vbc40040"
helpviewer_keywords: 
  - "BC40040"
ms.assetid: c640dd59-56a9-43ed-b199-32a60f7b9b06
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 泛型參數條件約束類型 &lt;類型名稱&gt; 不符合 CLS 標準
泛型類型標示為 `<CLSCompliant(True)>`，但其中一個類型參數的條件約束指定標示為 `<CLSCompliant(False)>` 類型、未標示，或因為不符合類型而不符資格。  
  
 為了讓類型符合 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 標準，它只能使用符合 CLS 標準的類型。 這也適用於泛型類型之類型參數上的條件約束。  
  
 下列 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 資料類型不符合 CLS 標準：  
  
-   [SByte Data Type](../Topic/SByte%20Data%20Type%20\(Visual%20Basic\).md)  
  
-   [UInteger Data Type](../Topic/UInteger%20Data%20Type.md)  
  
-   [ULong Data Type](../Topic/ULong%20Data%20Type%20\(Visual%20Basic\).md)  
  
-   [UShort Data Type](../Topic/UShort%20Data%20Type%20\(Visual%20Basic\).md)  
  
 將 <xref:System.CLSCompliantAttribute> 屬性套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40040  
  
### 更正這個錯誤  
  
-   如果泛型類型必須採用受限於這個特定類型的類型參數，請移除 <xref:System.CLSCompliantAttribute>。 類型不符合 CLS 標準。  
  
-   如果泛型類型必須符合 CLS 標準，請將這個條件約束的類型變更為最符合 CLS 標準的類型。 例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger`，則可能可以使用 `Integer`。 如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [\<PAVE OVER\> 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)