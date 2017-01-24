---
title: "編譯器錯誤 CS1662 | Microsoft Docs"
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
  - "CS1662"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1662"
ms.assetid: e61a4fc8-0ef1-4a4a-a27b-3a015c3ba38a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1662
無法將匿名方法區塊轉換成委派類型 'delegate type'，因為區塊中的某些傳回類型無法隱含地轉換成委派傳回類型。  
  
 如果匿名方法區塊的 return 陳述式有類型無法隱含地轉換為委派的傳回類型，就會發生此錯誤。  
  
 下列範例會產生 CS1662：  
  
```  
// CS1662.cs delegate int MyDelegate(int i); class C { public static void Main() { MyDelegate d = delegate(int i) { return 1.0; };  // CS1662 // Try this instead: // MyDelegate d = dekegate(int i) { return (int)1.0; }; } }  
```