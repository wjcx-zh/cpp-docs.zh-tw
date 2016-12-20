---
title: "編譯器錯誤 CS0074 | Microsoft Docs"
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
  - "CS0074"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0074"
ms.assetid: 9395c532-3934-4553-8e41-042bfe3399ce
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0074
'event': 抽象事件不能有初始設定式  
  
 如果[事件](../Topic/event%20\(C%23%20Reference\).md)標記為 **abstract**，則無法初始化。 如需詳細資訊，請參閱[事件](../Topic/Events%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0074：  
  
```  
// CS0074.cs delegate void D(); abstract class Test { public abstract event D e = null;   // CS0074 // try the following line instead // public abstract event D e; public static void Main() { } }  
```