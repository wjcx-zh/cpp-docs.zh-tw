---
title: "編譯器錯誤 CS0551 | Microsoft Docs"
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
  - "CS0551"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0551"
ms.assetid: fb456ecf-dff3-4e39-b9b3-de23d81dadea
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0551
明確介面實作 'implementation' 遺失存取子 'accessor'  
  
 明確實作介面屬性的類別必須實作該介面定義的所有存取子。  
  
 如需詳細資訊，請參閱[使用屬性](../Topic/Using%20Properties%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0551。  
  
```  
// CS0551.cs // compile with: /target:library interface ii { int i { get; set; } } public class a : ii { int ii.i { set {} }   // CS0551 // OK int ii.i { set {} get { return 0; } } }  
```