---
title: "編譯器錯誤 CS1002 | Microsoft Docs"
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
  - "CS1002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1002"
ms.assetid: 659b7abf-9311-40c9-9594-5372464c6148
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1002
必須是 ;  
  
 編譯器偵測到分號遺漏。 C\# 中的每個陳述式結尾都需要分號。 陳述式可能跨越多行。  
  
 下列範例會產生 CS1002：  
  
```  
// CS1002.cs namespace x { abstract public class clx { int i   // CS1002, missing semicolon public static int Main() { return 0; } } }  
```  
  
## 請參閱  
 [陳述式](../Topic/Statements%20\(C%23%20Programming%20Guide\).md)