---
title: "編譯器錯誤 CS1014 | Microsoft Docs"
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
  - "CS1014"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1014"
ms.assetid: 60c1e9af-5a0d-4ae0-a2e6-881b0d1535e9
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1014
必須是 get 或 set 存取子  
  
 在屬性宣告中找到方法宣告。 您只能在屬性中宣告 `get` 和 `set` 方法。  
  
 如需屬性的詳細資訊，請參閱[使用屬性](../Topic/Using%20Properties%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS1014。  
  
```  
// CS1014.cs // compile with: /target:library class Sample { public int TestProperty { get { return 0; } int z;   // CS1014  not get or set } }  
```