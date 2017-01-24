---
title: "編譯器錯誤 CS1015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1015"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1015"
ms.assetid: 53179feb-e8be-41e0-bb0b-f7879e9fa613
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1015
必須是物件、字串或類別類型。  
  
 已嘗試將預先定義的資料類型傳遞到 [catch](../Topic/try-catch%20\(C%23%20Reference\).md) 區塊。 只有衍生自 <xref:System.Exception?displayProperty=fullName> 的資料類型才能傳遞至 `catch` 區塊。 如需例外狀況的詳細資訊，請參閱 [例外狀況處理陳述式](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md)。  
  
## 範例  
 下列範例會產生 CS1015：  
  
```  
// CS1015.cs class Sample { static void Main() { try { } catch(int)   // CS1015, int is not derived from System.Exception { } } }  
```