---
title: "編譯器警告 (層級 1) CS1634 | Microsoft Docs"
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
  - "CS1634"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1634"
ms.assetid: 4fd00eeb-89e3-4c18-827d-9b00a4bd8c9a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1634
必須是 disable 或 restore  
  
 如果 \#pragma 警告子句格式不正確，例如，如果停用或已省略還原，就會發生此錯誤。 如需詳細資訊，請參閱 [\#pragma 警告](../Topic/%23pragma%20warning%20\(C%23%20Reference\).md)主題。  
  
## 範例  
 下列範例會產生 CS1634：  
  
```  
// CS1634.cs // compile with: /W:1 #pragma warning   // CS1634 // Try this instead: // #pragma warning disable 0219 class MyClass { public static void Main() { } }  
```