---
title: "&#39;&lt;項目名稱&gt;&#39; 已經過時：&#39;&lt;錯誤訊息&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40000"
  - "vbc40000"
helpviewer_keywords: 
  - "BC40000"
ms.assetid: dade0f57-eca1-4dd0-b978-020678838be6
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;項目名稱&gt;&#39; 已經過時：&#39;&lt;錯誤訊息&gt;&#39;
陳述式嘗試存取已使用 <xref:System.ObsoleteAttribute> 屬性和指示詞標記以視為警告的程式設計項目。  
  
 您可以將任何程式設計項目標記為不再使用，方法是對其套用 <xref:System.ObsoleteAttribute>。 如果您這麼做，則可以將屬性 \(attribute\) 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性 \(property\) 設定為 `True` 或 `False`。 如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。 如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。  
  
 根據預設，這個訊息是一個警告，因為 <xref:System.ObsoleteAttribute> 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性是 `False`。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40000  
  
### 更正這個錯誤  
  
1.  請檢查引用的錯誤訊息，並採取適當的動作。  
  
2.  確定原始程式碼參考正確拼寫項目名稱。  
  
## 請參閱  
 [不在組建中：Visual Basic 中使用的屬性](http://msdn.microsoft.com/zh-tw/22231318-8a40-49af-9245-e0aab723563b)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)