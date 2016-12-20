---
title: "編譯器錯誤 CS1518 | Microsoft Docs"
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
  - "CS1518"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1518"
ms.assetid: 26e0870d-fe91-4c66-b3f8-ed2b074c964e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1518
必須是類別、委派、列舉、介面或結構  
  
 在[命名空間](../Topic/namespace%20\(C%23%20Reference\).md)中，找到不支援的宣告。 在命名空間內，編譯器只會接受類別、結構、列舉、介面、命名空間和委派。  
  
## 範例  
 下列範例會產生 CS1518：  
  
```  
// CS1518.cs namespace x { sealed class c1 {};      // OK namespace f2 {};         // OK sealed f3 {};            // CS1518 }  
```