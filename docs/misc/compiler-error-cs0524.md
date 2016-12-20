---
title: "編譯器錯誤 CS0524 | Microsoft Docs"
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
  - "CS0524"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0524"
ms.assetid: a5cd8fb0-f5df-4580-9116-a6be4dffd1cb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0524
'type': 介面不能宣告類型  
  
 [interface](../Topic/interface%20\(C%23%20Reference\).md) 不能包含使用者定義的類型；它應該只包含方法和屬性。  
  
## 範例  
 下列範例會產生 CS0524：  
  
```  
// CS0524.cs public interface Clx { public class Cly   // CS0524, delete user-defined type { } }  
  
```