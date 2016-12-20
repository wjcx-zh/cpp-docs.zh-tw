---
title: "編譯器錯誤 CS1733 | Microsoft Docs"
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
  - "CS1733"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1733"
ms.assetid: 2188aabe-404d-4a95-a11a-736dbd848508
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1733
必須是運算式。  
  
 當編譯器在發生錯誤的該行上需要有運算式時，就會產生這個錯誤。 在下列範例中，初始設定式中的尾端逗號向編譯器指出後面接著另一個運算式。  
  
### 更正這個錯誤  
  
-   提供遺漏的運算式。  
  
-   移除造成編譯器需要運算式的語彙基元。  
  
## 範例  
 下列範例會產生 CS1733，因為尾端出現逗號：  
  
```  
// cs1733.cs using System.Collections.Generic; public class Test { public static void Main() { List<int> list = new List<int>() {{ 1, 2, }};// CS1733 } }  
```