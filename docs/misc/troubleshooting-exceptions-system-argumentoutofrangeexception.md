---
title: "疑難排解例外狀況：System.ArgumentOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ArgumentOutOfRangeException 類別"
ms.assetid: f53c58d9-7c4e-407f-93d3-1e59d90d98f5
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.ArgumentOutOfRangeException
當方法被叫用，但傳遞至該方法的引數至少有一個不是 null 參考 \(在 Visual Basic 中為 <xref:System.ArgumentOutOfRangeException>\) 而且沒有包含有效的值，就會擲回 `Nothing`。  
  
## 相關秘訣  
 **請確定傳遞至這個方法的所有引數，都具有被叫用方法所定義的有效值。**  
 不是 null 參考的引數必須包含有效的值。  
  
 **如果您要使用集合，請確定索引必須小於集合的大小。**  
 索引必須在集合的大小範圍內，而且不能超過其大小範圍或小於零。 如需詳細資訊，請參閱[集合](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 **使用 ComboBox 或 ListBox 類別的多載雙引數 FindString 或 FindStringExact 方法時，請檢查 startIndex 參數**。  
 如果 `startIndex` 等於相關清單最後一個項目的索引值，就會擲回這個例外狀況。 若要解決這個問題，請傳遞 0 做為 `startIndex` 參數，或使用單一引數 `FindString` 或 `FindStringExact` 方法。 如需詳細資訊，請參閱 [CComboBox::FindString](../Topic/CComboBox::FindString.md)或 [CListBox::FindString](../Topic/CListBox::FindString.md)。  
  
## 請參閱  
 <xref:System.ArgumentOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)