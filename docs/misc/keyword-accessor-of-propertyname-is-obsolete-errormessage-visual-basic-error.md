---
title: "&#39;&lt;屬性名稱&gt;&#39; 的 &#39;&lt;關鍵字&gt;&#39; 存取子已經過時: &#39;&lt;錯誤訊息&gt;&#39; (Visual Basic 錯誤) | Microsoft Docs"
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
  - "vbc30911"
  - "bc30911"
helpviewer_keywords: 
  - "BC30911"
ms.assetid: b690be0c-4dca-4f79-88ed-4ee3e3f1f90b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;屬性名稱&gt;&#39; 的 &#39;&lt;關鍵字&gt;&#39; 存取子已經過時: &#39;&lt;錯誤訊息&gt;&#39; (Visual Basic 錯誤)
已使用 <xref:System.ObsoleteAttribute> 屬性 \(attribute\) 和指示詞標記其對應程序之讀取或寫入屬性 \(property\) 的陳述式嘗試，會視為錯誤。  
  
 您可以將任何程式設計項目標記為不再使用，方法是對其套用 <xref:System.ObsoleteAttribute>。 如果您這麼做，則可以將屬性 \(attribute\) 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性 \(property\) 設定為 `True` 或 `False`。 如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。 如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。  
  
 **錯誤 ID︰**BC30911  
  
### 更正這個錯誤  
  
1.  請檢查引用的錯誤訊息，並採取適當的動作。  
  
2.  請確定原始程式碼參考正確拼寫的屬性名稱。  
  
3.  請避免使用產生這則訊息的方式 \(讀取或寫入\) 來存取屬性。  
  
## 請參閱  
 [不在組建中：Visual Basic 中使用的屬性](http://msdn.microsoft.com/zh-tw/22231318-8a40-49af-9245-e0aab723563b)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)