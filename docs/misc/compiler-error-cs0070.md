---
title: "編譯器錯誤 CS0070 | Microsoft Docs"
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
  - "CS0070"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0070"
ms.assetid: bb0de7c6-c734-4a8f-ab62-0a50eac2a91f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0070
事件 'event' 只能出現在 \+\= 或 \-\= 的左邊 \(除非從類型 'type' 中使用\)  
  
 [事件](../Topic/event%20\(C%23%20Reference\).md)在其定義所在的類別之外只能加減參考。 如需詳細資訊，請參閱[事件](../Topic/Events%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0070：  
  
```  
// CS0070.cs using System; public delegate void EventHandler(); public class A { public event EventHandler Click; public static void OnClick() { EventHandler eh; A a = new A(); eh = a.Click; } public static void Main() { } } public class B { public int Foo () { EventHandler eh = new EventHandler(A.OnClick); A a = new A(); eh = a.Click;   // CS0070 // try the following line instead // a.Click += eh; return 1; } }  
```