---
title: "疑難排解例外狀況：System.OverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "OverflowException 類別"
ms.assetid: bd380db7-5d05-4d7f-be5b-e654fdadf14c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.OverflowException
當檢查內容中的算術、轉型或轉換運算造成溢位時，就會擲回 <xref:System.OverflowException> 例外狀況。 當運算所產生的目的型別值太大時、無限大，或者不是數字 \(NaN\) 時，就會發生溢位。  
  
## 相關秘訣  
 **從數值轉型時，這個值必須是小於無限大的有效的值。**  
 來源值不能是無限大或不是數字。  
  
 **請確定沒有除以零的情況。**  
 除以零通常會導致這個例外狀況。  
  
## 備註  
 在偵測溢位的語言中，發生溢位時所擲回的例外狀況會是 <xref:System.OverflowException>。 例如，在 C\# 中，用來偵測溢位狀況的是 `checked` 關鍵字。<xref:System.OverflowException> 例外狀況只會發生在檢查的內容中。  
  
 從整數、十進位類型的算術運算或目的型別範圍外的轉換，所得到的結果為：  
  
-   如果運算是常數運算式，則在檢查的內容中會發生編譯時期錯誤。 否則，如果運算是在執行階段執行，就會擲回 <xref:System.OverflowException> 例外狀況。  
  
-   在未經檢查的內容中，以捨棄任何不適合在目的型別中的高序位位元之方式，刪去結果。  
  
 如需資料類型之值範圍的相關資訊，請參閱[Data Types](../Topic/Data%20Type%20Summary%20\(Visual%20Basic\).md)、[整數類資料類型表](../Topic/Integral%20Types%20Table%20\(C%23%20Reference\).md) 或[浮點類型表](../Topic/Floating-Point%20Types%20Table%20\(C%23%20Reference\).md)。  
  
## 請參閱  
 <xref:System.OverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)