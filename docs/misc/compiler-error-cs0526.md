---
title: "編譯器錯誤 CS0526 | Microsoft Docs"
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
  - "CS0526"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0526"
ms.assetid: befc46b4-28ea-40d3-89ac-132b92455772
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0526
介面不能包含建構函式  
  
 無法為[介面](../Topic/interface%20\(C%23%20Reference\).md)定義建構函式。 如果方法的名稱與類別的名稱相同，但沒有傳回值，則會將它視為建構函式。  
  
 下列範例會產生 CS0526：  
  
```  
// CS0526.cs namespace x { public interface clx { public clx()   // CS0526 { } } public class cly { public static void Main() { } } }  
```