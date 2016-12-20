---
title: "&#39;System.Nullable&#39; 未滿足類型參數 &#39;&lt;類型參數名稱&gt;&#39; 的 &#39;Structure&#39; 條件約束 | Microsoft Docs"
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
  - "bc32115"
  - "vbc32115"
helpviewer_keywords: 
  - "BC32115"
ms.assetid: 98053645-fa76-4826-a7c1-f1bdf3511863
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Nullable&#39; 未滿足類型參數 &#39;&lt;類型參數名稱&gt;&#39; 的 &#39;Structure&#39; 條件約束
已叫用泛型類型，以傳遞 <xref:System.Nullable%601> 類型引數至含 `Structure` 條件約束的類型參數。  
  
 Common Language Runtime \(CLR\) 特別不允許 <xref:System.Nullable%601> 結構作為本身的類型引數。 即使它是一種結構，或滿足 `Structure` 條件約束，但以遞迴方式使用可能會導致結構冗長，例如 `Nullable(Of Nullable(Of Nullable))`。  
  
 **錯誤 ID：**BC32115  
  
### 更正這個錯誤  
  
-   移除類型參數的 `Structure` 條件約束，或將類型引數變更為 <xref:System.Nullable%601> 以外的實值類型。  
  
## 請參閱  
 <xref:System.Nullable%601>   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [結構 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)