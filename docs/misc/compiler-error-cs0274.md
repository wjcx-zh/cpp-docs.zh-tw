---
title: "編譯器錯誤 CS0274 | Microsoft Docs"
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
  - "CS0274"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0274"
ms.assetid: bbd2d64e-a756-4713-b9ed-711d50b65e00
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0274
不可同時對屬性或索引子 'property\/indexer' 的兩個存取子，指定存取範圍修飾詞  
  
 當您在屬性或索引子的兩個存取子上，使用存取修飾詞來宣告該屬性或索引子時，就會發生這個錯誤。 若要解決這個錯誤，請只對兩個存取子的其中之一使用存取修飾詞。 如需詳細資訊，請參閱[存取子的存取範圍](../Topic/Restricting%20Accessor%20Accessibility%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0274：  
  
```  
// CS0274.cs public class MyClass { public int Property   // CS0274 { public get { return 0; } protected set { } } }  
```