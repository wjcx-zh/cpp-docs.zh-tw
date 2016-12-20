---
title: "編譯器錯誤 CS0079 | Microsoft Docs"
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
  - "CS0079"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0079"
ms.assetid: 71c85883-b72f-402f-a828-18ca92976273
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0079
事件 'event' 只可以出現在 \+\= 或 \-\= 左邊  
  
 未正確地呼叫[事件](../Topic/event%20\(C%23%20Reference\).md)。 如需詳細資訊，請參閱[事件](../Topic/Events%20\(C%23%20Programming%20Guide\).md)與[委派](../Topic/Delegates%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0079：  
  
```  
// CS0079.cs using System; public delegate void MyEventHandler(); public class Class1 { private MyEventHandler _e; public event MyEventHandler Pow { add { _e += value; Console.WriteLine("in add accessor"); } remove { _e -= value; Console.WriteLine("in remove accessor"); } } public void Handler() { } public void Fire() { if (_e != null) { Pow();   // CS0079 // try the following line instead // _e(); } } public static void Main() { Class1 p = new Class1(); p.Pow += new MyEventHandler(p.Handler); p._e(); p.Pow += new MyEventHandler(p.Handler); p._e(); p._e -= new MyEventHandler(p.Handler); if (p._e != null) { p._e(); } p.Pow -= new MyEventHandler(p.Handler); if (p._e != null) { p._e(); } } }  
```