---
title: "根命名空間 &lt;命名空間名稱&gt; 不符合 CLS 標準 | Microsoft Docs"
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
  - "bc40038"
  - "vbc40038"
helpviewer_keywords: 
  - "BC40038"
ms.assetid: ec850295-b2fe-4f19-b808-d22fe0aaa32d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 根命名空間 &lt;命名空間名稱&gt; 不符合 CLS 標準
組件標記為 `<CLSCompliant(True)>`，但根命名空間名稱開頭為底線 \(`_`\)。  
  
 程式設計項目可以包含一或多個底線，但若要遵守 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\)，它不得以底線為開頭。 請參閱 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)。  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40038  
  
### 更正這個錯誤  
  
-   如需 CLS 符合性，請變更根命名空間名稱，使它不是以底線開頭。  
  
-   如果您需要根命名空間名稱保持不變，那麼請從組件移除 <xref:System.CLSCompliantAttribute>或將它標記為 `<CLSCompliant(False)>`。  
  
## 請參閱  
 [Namespace Statement](../Topic/Namespace%20Statement.md)   
 [Visual Basic 中的命名空間](../Topic/Namespaces%20in%20Visual%20Basic.md)   
 [\/rootnamespace](../Topic/-rootnamespace.md)   
 [NIB: 如何：變更應用程式的命名空間 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/029d85c0-e173-4f7a-afba-a29f3aaf6ebf)   
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [Visual Basic Naming Conventions](../Topic/Visual%20Basic%20Naming%20Conventions.md)   
 [\<PAVE OVER\> 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)