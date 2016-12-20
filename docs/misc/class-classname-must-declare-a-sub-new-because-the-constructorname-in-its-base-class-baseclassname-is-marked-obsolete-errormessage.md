---
title: "類別 &#39;&lt;類別名稱&gt;&#39; 必須宣告 &#39;Sub New&#39;，因為 &#39;&lt;建構函式名稱&gt;&#39; 在它的基底類別 &#39;&lt;基底類別名稱&gt;&#39; 中標示為過時：&#39;&lt;錯誤訊息&gt;&#39; | Microsoft Docs"
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
  - "bc30918"
  - "vbc30918"
helpviewer_keywords: 
  - "BC30918"
ms.assetid: 4879254c-4b03-4416-a4a3-e9f6b5d92a1a
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類別 &#39;&lt;類別名稱&gt;&#39; 必須宣告 &#39;Sub New&#39;，因為 &#39;&lt;建構函式名稱&gt;&#39; 在它的基底類別 &#39;&lt;基底類別名稱&gt;&#39; 中標示為過時：&#39;&lt;錯誤訊息&gt;&#39;
類別宣告不包括建構函式，且基底類別建構函式已使用 <xref:System.ObsoleteAttribute> 屬性和指示詞標記，以將其視為錯誤。  
  
 當衍生類別未宣告建構函式時，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 會嘗試產生呼叫 `MyBase.New()` 的隱含無參數建構函式。 如果可以不使用引數呼叫的基底類別中沒有可存取的建構函式，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 就無法產生隱含的建構函式。 在這種情況下，會使用 <xref:System.ObsoleteAttribute> 屬性標記必要的建構函式，因此 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 無法呼叫它。  
  
 您可以將任何程式設計項目標記為不再使用，方法是對其套用 <xref:System.ObsoleteAttribute>。 如果您這麼做，則可以將屬性 \(attribute\) 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性 \(property\) 設定為 `True` 或 `False`。 如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。 如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。  
  
 **錯誤 ID︰**BC30918  
  
### 更正這個錯誤  
  
1.  請檢查引用的錯誤訊息，並採取適當的動作。  
  
2.  使用 `Sub New` 宣告衍生類別中的建構函式。  
  
## 請參閱  
 [不在組建中：Visual Basic 中使用的屬性](http://msdn.microsoft.com/zh-tw/22231318-8a40-49af-9245-e0aab723563b)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)