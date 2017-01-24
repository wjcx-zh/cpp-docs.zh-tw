---
title: "編譯器錯誤 CS0442 | Microsoft Docs"
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
  - "CS0442"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0442"
ms.assetid: a411660d-0db6-4b63-b19e-f4538fc201e5
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0442
'Property': 抽象屬性不能有私用存取子  
  
 當您使用存取修飾詞 "private" 修改抽象存取子時，會發生這個錯誤。 若要解決，請使用不同的存取修飾詞，或將屬性設為非抽象。  
  
## 範例  
 下列範例會產生 CS0442：  
  
```  
// CS0442.cs public abstract class MyClass { public abstract int AbstractProperty { get; private set;   // CS0442 // Try this instead: // set; } }  
```