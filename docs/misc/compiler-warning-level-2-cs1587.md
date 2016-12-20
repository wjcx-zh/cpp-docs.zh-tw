---
title: "編譯器警告 (層級 2) CS1587 | Microsoft Docs"
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
  - "CS1587"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1587"
ms.assetid: b27c2009-d485-43fd-a649-fbc15570d256
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS1587
XML 註解沒有放置在有效的語言項目前  
  
 並非所有語言項目上都可以有建議使用的文件註解標記。 例如，命名空間上不允許有標記。 如需 XML 註解的詳細資訊，請參閱[建議使用的文件註解標籤](../Topic/Recommended%20Tags%20for%20Documentation%20Comments%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS1587：  
  
```  
// CS1587.cs // compile with: /W:2 /doc:x.xml /// <summary>test</summary>   // CS1587, tag not allowed on namespace namespace MySpace { class MyClass { public static void Main() { } } }  
```