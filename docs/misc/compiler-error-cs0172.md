---
title: "編譯器錯誤 CS0172 | Microsoft Docs"
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
  - "CS0172"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0172"
ms.assetid: 1272c575-3580-4897-95fb-83f45d7435ae
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0172
無法判斷條件運算式的類型，因為 'type1' 和 'type2' 會互相隱含轉換。  
  
 在條件陳述式中，您必須可以轉換 `:` 運算子任一側的類型。 此外，不能有相互轉換常式；您只需要一個轉換。 如需詳細資訊，請參閱[轉換運算子](../Topic/Conversion%20Operators%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0172：  
  
```  
// CS0172.cs public class Square { public class Circle { public static implicit operator Circle(Square aa) { return null; } public static implicit operator Square(Circle aa) // using explicit resolves this error // public static explicit operator Square(Circle aa) { return null; } } public static void Main() { Circle aa = new Circle(); Square ii = new Square(); object o = (1 == 1) ? aa : ii;   // CS0172 // the following cast would resolve this error // (1 == 1) ? aa : (Circle)ii; } }  
```