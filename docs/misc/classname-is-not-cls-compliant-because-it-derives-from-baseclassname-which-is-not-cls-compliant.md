---
title: "&#39;&lt;類別名稱&gt;&#39; 不符合 CLS 標準，因為其衍生自不符合 CLS 標準的 &#39;&lt;基底類別名稱&gt;&#39; | Microsoft Docs"
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
  - "vbc40026"
  - "bc40026"
helpviewer_keywords: 
  - "BC40026"
ms.assetid: debcd5e4-75e7-4b14-a6cc-18f1009fe52c
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;類別名稱&gt;&#39; 不符合 CLS 標準，因為其衍生自不符合 CLS 標準的 &#39;&lt;基底類別名稱&gt;&#39;
當類別或介面衍生自或實作標記為 `<CLSCompliant(False)>` 或未標記的類型時，則標記為 `<CLSCompliant(True)>`。  
  
 類別或介面若要符合 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 標準，其整個繼承階層都必須符合標準。 這表示它直接或間接繼承的每個類型都必須符合標準。 同樣地，如果類別實作一或多個介面，則它們在整個繼承階層都必須符合標準。  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40026  
  
### 更正這個錯誤  
  
-   如果您必須符合 CLS 標準，請在不同的繼承階層或實作配置內定義這個類型。  
  
-   如果您想要將這個類型保留在其目前繼承階層或實作配置內，請從其定義移除 <xref:System.CLSCompliantAttribute> 或將其標記為 `<CLSCompliant(False)>`。  
  
## 請參閱  
 [\<PAVE OVER\> 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)