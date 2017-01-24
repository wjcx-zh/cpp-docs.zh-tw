---
title: "類型 &#39;&lt;類型名稱1&gt;&#39; 的運算式不能屬於類型 &#39;&lt;類型名稱2&gt;&#39; | Microsoft Docs"
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
  - "vbc31430"
  - "bc31430"
helpviewer_keywords: 
  - "BC31430"
ms.assetid: 1d527033-3f6f-4945-b1d3-5ef59a1e1b53
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;&lt;類型名稱1&gt;&#39; 的運算式不能屬於類型 &#39;&lt;類型名稱2&gt;&#39;
`TypeOf`...`Is` 運算式會測試指向其未包含之資料類型的物件參考變數。  
  
 在某些情況下，編譯器可決定 `TypeOf`...`Is` 測試只會失敗；例如，如果兩個類別之間沒有任何繼承關聯性。  
  
 下列程式碼可能會產生此錯誤。  
  
 `Dim refVar as System.Windows.Forms.Form`  
  
 `If TypeOf refVar Is System.Array`  
  
 `End If`  
  
 由於 <xref:System.Windows.Forms.Form> 和 <xref:System.Array> 是完全不相關的類型，因此編譯器可決定讓 `TypeOf`...`Is` 運算式針對 `refVar` 的任何值傳回 `False`。  
  
 **錯誤 ID︰**BC31430  
  
### 更正這個錯誤  
  
-   測試變數中的實際資料類型，或是完全移除 `TypeOf`...`Is` 測試。  
  
## 請參閱  
 [TypeOf Operator](../Topic/TypeOf%20Operator%20\(Visual%20Basic\).md)   
 [How to: Determine What Type an Object Variable Refers To](../Topic/How%20to:%20Determine%20What%20Type%20an%20Object%20Variable%20Refers%20To%20\(Visual%20Basic\).md)