---
title: "對於 &#39;|1&#39; 的某個其他部分類型所定義的對應類型參數的條件約束而言，這個類型參數的條件約束不相符。 | Microsoft Docs"
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
  - "vbc30932"
  - "bc30932"
helpviewer_keywords: 
  - "BC30932"
ms.assetid: a38ca4ad-6bbf-421e-a0d7-c5e0a9029160
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 對於 &#39;|1&#39; 的某個其他部分類型所定義的對應類型參數的條件約束而言，這個類型參數的條件約束不相符。
當您分割數個宣告中類別或結構的定義時，編譯器會將類別或結構視為其所有部分宣告的聯集。 因此，您無法在各種部分宣告中定義任何衝突的修飾詞或類型參數清單。  
  
 **錯誤 ID︰**BC30932  
  
### 更正這個錯誤  
  
1.  判斷您類別或結構所需的類型參數清單。 這包括參數、其順序和其條件約束清單。  
  
2.  請確定每個部分定義都使用相同的類型參數清單。  
  
## 請參閱  
 [Partial](../Topic/Partial%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)