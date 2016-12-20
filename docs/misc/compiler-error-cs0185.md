---
title: "編譯器錯誤 CS0185 | Microsoft Docs"
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
  - "CS0185"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0185"
ms.assetid: d6546e10-0af3-4860-8e6f-2da7dbeb3d28
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0185
'type' 不是 lock 陳述式需要的參考類型  
  
 [lock](../Topic/lock%20Statement%20\(C%23%20Reference\).md) 陳述式只能評估參考類型。 如需詳細資訊，請參閱[執行緒同步處理](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)與[參考類型](../Topic/Reference%20Types%20\(C%23%20Reference\).md)。  
  
## 範例  
 下列範例會產生 CS0185：  
  
```  
// CS0185.cs public class MainClass { public static void Main () { lock (1)   // CS0185 // try the following lines instead // MainClass x = new MainClass(); // lock(x) { } } }  
```