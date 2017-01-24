---
title: "疑難排解例外狀況：System.RankException | Microsoft Docs"
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
  - "RankException 類別"
ms.assetid: ad7aa34a-f84b-4650-aaec-a75a8b85c50f
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.RankException
當具有錯誤維度數目的陣列傳遞至方法時，就會擲回 <xref:System.RankException> 例外狀況。  
  
## 相關秘訣  
 **請確定陣列擁有所需的維度數目。**  
 如需詳細資訊，Visual Basic 使用者請參閱 [Array Dimensions in Visual Basic](../Topic/Array%20Dimensions%20in%20Visual%20Basic.md)。  
  
 如需詳細資訊，C\# 使用者請參閱[陣列](../Topic/Arrays%20\(C%23%20Programming%20Guide\).md)。  
  
## 備註  
 由於陣列註標起始為 0，每個維度的最低可用註標永遠為 0。  
  
## 請參閱  
 <xref:System.RankException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [陣列](../Topic/Arrays%20in%20Visual%20Basic.md)