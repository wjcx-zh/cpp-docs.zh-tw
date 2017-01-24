---
title: "編譯器錯誤 CS0550 | Microsoft Docs"
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
  - "CS0550"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0550"
ms.assetid: 57278c17-443c-40f2-9ebd-853558743564
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0550
'accessor' 加入了在介面成員 'property' 中找不到的存取子  
  
 在衍生類別中，屬性的實作包含未在基底介面中指定的存取子。  
  
 如需詳細資訊，請參閱[使用屬性](../Topic/Using%20Properties%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0550：  
  
```  
// CS0550.cs namespace x { interface ii { int i { get; // add the following accessor to resolve this CS0550 // set; } } public class a : ii { int ii.i { get { return 0; } set {}   // CS0550  no set in interface } public static void Main() {} } }  
```