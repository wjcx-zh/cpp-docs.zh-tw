---
title: "編譯器錯誤 CS1646 | Microsoft Docs"
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
  - "CS1646"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1646"
ms.assetid: 5e4b0f1e-8de3-42b0-bde6-9f882677a409
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1646
逐字規範 "@" 之後應接著關鍵字、識別項或字串。  
  
 查看逐字規範 '@' 在字串常值中的使用方式。 逐字規範只能在字串、關鍵字或識別項之前。 若要解決這個錯誤，請移除任何不當位置中的 @ 符號，或是加入預期的字串、關鍵字或識別項。  
  
 下列範例會產生 CS1646：  
  
```  
// CS1646 class C { int i = @5;  // CS1646 // Try this line instead: // int i = 5; }  
```