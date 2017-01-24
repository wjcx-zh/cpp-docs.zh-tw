---
title: "編譯器錯誤 CS0664 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0664"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0664"
ms.assetid: 60fe15a7-db22-414f-a7b8-fac79dad22b4
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0664
不能隱含將類型 double 的常值轉換為類型 'type'; 請使用 'suffix' 後置字元來建立此類型的常值  
  
 無法完成指派；請使用後置字元來更正指令。 每個類型的文件可識別類型的對應後置字元。 如需轉換的詳細資訊，請參閱[轉型和類型轉換](../Topic/Casting%20and%20Type%20Conversions%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0664：  
  
```c#  
// CS0664.cs class Example { static void Main() { decimal d1 = 1.0;   // CS0664, because 1.0 is interpreted // as a double. // Try the following line instead. decimal d2 = 1.0M;  // The M tells the compiler that 1.0 is a // decimal. Console.WriteLine(d2); } }  
```  
  
## 請參閱  
 [類型轉換表](../Topic/Type%20Conversion%20Tables%20in%20the%20.NET%20Framework.md)