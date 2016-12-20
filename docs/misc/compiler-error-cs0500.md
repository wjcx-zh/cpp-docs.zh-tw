---
title: "編譯器錯誤 CS0500 | Microsoft Docs"
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
  - "CS0500"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0500"
ms.assetid: b1a45708-702b-482c-bd71-c0c2531e29f3
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0500
因為標記成 abstract，'class member' 無法宣告主體  
  
 [abstract](../Topic/abstract%20\(C%23%20Reference\).md) 方法不能包含其實作。  
  
 下列範例會產生 CS0500：  
  
```  
// CS0500.cs namespace x { abstract public class clx { abstract public void f(){}   // CS0500 // try the following line instead // abstract public void f(); } public class cly { public static int Main() { return 0; } } }  
```