---
title: "&#39;&lt;成員名稱&gt;&#39; 已經過時：&#39;&lt;錯誤訊息&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30668"
  - "vbc30668"
helpviewer_keywords: 
  - "BC30668"
ms.assetid: 25e5606c-2734-4f42-a2bc-1ad28ec1e892
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;成員名稱&gt;&#39; 已經過時：&#39;&lt;錯誤訊息&gt;&#39;
陳述式嘗試存取已使用 <xref:System.ObsoleteAttribute> 屬性和指示詞標記的類別或結構成員，以將其視為錯誤。  
  
 您可以將任何程式設計項目標記為不再使用，方法是對其套用 <xref:System.ObsoleteAttribute>。 如果您這麼做，則可以將屬性 \(attribute\) 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性 \(property\) 設定為 `True` 或 `False`。 如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。 如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。  
  
 **錯誤 ID︰**BC30668  
  
### 更正這個錯誤  
  
1.  請檢查引用的錯誤訊息，並採取適當的動作。  
  
2.  確定原始程式碼參考正確拼寫成員名稱。  
  
## 請參閱  
 [不在組建中：Visual Basic 中使用的屬性](http://msdn.microsoft.com/zh-tw/22231318-8a40-49af-9245-e0aab723563b)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)