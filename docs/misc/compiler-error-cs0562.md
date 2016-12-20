---
title: "編譯器錯誤 CS0562 | Microsoft Docs"
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
  - "CS0562"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0562"
ms.assetid: dceecce5-90ce-4554-820c-f4c06b2b8258
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0562
一元運算子的參數必須為包含類型  
  
 運算子多載的方法宣告必須遵循特定的指導方針。 如需詳細資訊，請參閱[多載運算子](../Topic/Overloadable%20Operators%20\(C%23%20Programming%20Guide\).md)和[Operator Overloading Sample](http://msdn.microsoft.com/zh-tw/1c6b4610-0a49-4532-8fa7-f694cfc65743)。  
  
## 範例  
 下列範例會產生 CS0562：  
  
```  
// CS0562.cs public class iii { public static implicit operator int(iii x) { return 0; } public static implicit operator iii(int x) { return null; } public static iii operator +(int aa)   // CS0562 // try the following line instead // public static iii operator +(iii aa) { return (iii)0; } public static void Main() { } }  
```