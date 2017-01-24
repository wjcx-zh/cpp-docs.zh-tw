---
title: "編譯器錯誤 CS0666 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0666"
ms.assetid: 44ad4574-b4a2-487b-8d05-0116762231ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0666
'member': 在結構中宣告了新的 protected 成員  
  
 [struct](../Topic/struct%20\(C%23%20Reference\).md) 不能是 [abstract](../Topic/abstract%20\(C%23%20Reference\).md) 而且一律隱含地 [sealed](../Topic/sealed%20\(C%23%20Reference\).md)。 因為結構不支援繼承，所以結構中 [protected](../Topic/protected%20\(C%23%20Reference\).md) 成員的概念沒有意義。 如需詳細資訊，請參閱[繼承](../Topic/Inheritance%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0666：  
  
```  
// CS0666.cs class M { static void Main() { } } struct S { protected int x;   // CS0666 }  
```