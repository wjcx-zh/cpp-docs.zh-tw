---
title: "編譯器錯誤 CS0539 | Microsoft Docs"
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
  - "CS0539"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0539"
ms.assetid: 41b8975c-abd1-4a36-98a4-8efa5fb0502a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0539
在明確介面宣告中的 'member' 不是介面成員  
  
 嘗試明確宣告不存在的[介面](../Topic/interface%20\(C%23%20Reference\).md)成員。 您應該刪除或變更宣告，讓它參考有效的介面成員。  
  
 下列範例會產生 CS0539：  
  
```  
// CS0539.cs namespace x { interface I { void m(); } public class clx : I { void I.x()   // CS0539 { } public static int Main() { return 0; } } }  
```