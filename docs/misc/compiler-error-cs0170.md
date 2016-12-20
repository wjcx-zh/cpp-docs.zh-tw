---
title: "編譯器錯誤 CS0170 | Microsoft Docs"
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
  - "CS0170"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0170"
ms.assetid: ba881e38-2abf-4a5f-b9e6-28d26a5bd235
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0170
使用可能未指派的欄位 'field'  
  
 在結構中使用了欄位，但未先加以初始化。 若要解決這個問題，請先判斷哪個欄位未初始化，然後加以初始化，再嘗試存取。 如需初始化結構的詳細資訊，請參閱[結構](../Topic/Structs%20\(C%23%20Programming%20Guide\).md) 和[使用結構](../Topic/Using%20Structs%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0170：  
  
```  
// CS0170.cs public struct error { public int i; } public class MyClass { public static void Main() { error e; // uncomment the next line to resolve this error // e.i = 0; System.Console.WriteLine( e.i );   // CS0170 because //e.i was never assigned } }  
```