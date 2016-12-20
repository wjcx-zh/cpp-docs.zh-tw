---
title: "編譯器錯誤 CS0066 | Microsoft Docs"
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
  - "CS0066"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0066"
ms.assetid: 9b50b49b-78b8-4562-8839-d59e5edbec6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0066
'event': 事件必須為委派類型  
  
 event 關鍵字需要[委派](../Topic/delegate%20\(C%23%20Reference\).md)類型。 如需詳細資訊，請參閱[事件](../Topic/Events%20\(C%23%20Programming%20Guide\).md)與[委派](../Topic/Delegates%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0066：  
  
```  
// CS0066.cs using System; public class EventHandler { } // to fix the error, remove the event declaration and the // EventHandler class declaration, and uncomment the following line // public delegate void EventHandler(); public class a { public event EventHandler Click;   // CS0066 private void TestMethod() { if (Click != null) Click(); } public static void Main() { } }  
```