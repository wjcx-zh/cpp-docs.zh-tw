---
title: "編譯器錯誤 CS1667 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1667"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1667"
ms.assetid: 59f64828-58bc-487c-862a-75537e21d4ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1667
屬性 'attribute' 對屬性或事件存取子無效。 它只對 'declaration type' 宣告有效。  
  
 如果您對屬性或事件存取子使用屬性，而它應該放在屬性或事件本身時，就會發生這個錯誤。 這個錯誤可能會因為屬性 <xref:System.CLSCompliantAttribute>、<xref:System.Diagnostics.ConditionalAttribute> 和 <xref:System.ObsoleteAttribute> 而發生。  
  
## 範例  
 下列範例會產生 CS1670：  
  
```  
// CS1667.cs using System; public class C { private int i; //Try this instead: //[Obsolete] public int ObsoleteProperty { [Obsolete]  // CS1667 get { return i; } set { i = value; } } public static void Main() { } }  
```